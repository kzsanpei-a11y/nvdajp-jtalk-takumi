# 変更点

## 公開版の決定：SLTを除外した12声ビルド（2026-11-16）

公開する成果物は、声が全12（V1〜V12）のビルド `nvdajp-jtalk-2026.3.1jp-takumi-mei.nvda-addon` です。

感情ラインナップ版（V1〜V13）には英語音声SLT（V13）を実験的に収録しましたが、作者の実機確認で、超高速の喋りと「バリバリ」という雑音になるだけで音声として成立しないことが分かりました（下の「実機確認の結果」参照）。そのため公開版からは、SLTの音声ファイル（`synthDrivers/jtalk/slt/`）、ドライバーのV13エントリ、`CREDIT-slt.txt` を取り除きました。それ以外の内容は感情ラインナップ版と同一で、デフォルトの声（V4）も変更していません。SLT入り版は作者の手元に実験用として残します。

`source/jtalkDriver.py` は公開版（V1〜V12）のドライバーに差し替え済みです。

土台：公式リリース `nvdajp-jtalk-2026.3.1jp.nvda-addon`（NVDA日本語版 2026.3.1jp のJTalkアドオン）

この土台に対して行った変更は、次の2点だけです。

## 1. 音声ファイルの追加

`synthDrivers/jtalk/takumi/` フォルダを新設し、次を入れました。

- `takumi_normal.htsvoice`
- `takumi_happy.htsvoice`
- `takumi_angry.htsvoice`
- `takumi_sad.htsvoice`
- `COPYRIGHT.txt`（Takumiのライセンス表記、配布物の実物）
- `README.txt`（配布物の実物）

あわせて、アドオン直下に `CREDIT-takumi.txt` を置きました。

音声条件は各ファイルの埋め込みヘッダーから実測しました。4ファイルとも同一条件です。

- SAMPLING_FREQUENCY: 48000
- FRAME_PERIOD: 240
- ALPHA: 0.55

## 2. ドライバーの声一覧への追加

`synthDrivers/jtalk/jtalkDriver.py` の `_jtalk_voices` に、V5〜V8の4エントリを追加しました。

- V5: takumi（takumi_normal.htsvoice）
- V6: takumi_happy
- V7: takumi_angry
- V8: takumi_sad

パラメータの起点は、既存のM001（V1）と同じ考え方で、lf0_base 5.0、pitch_bias 0、speaker_attenuation 1.0、beta 0.00とし、alphaは実測値0.55を用いました。デフォルトの声（V4）は変更していません。

改変後のドライバー全文は `source/jtalkDriver.py` に収録しています。

## 検証（ビルド時）

- 土台アドオンの収録ファイルとの一覧比較で、欠落がないこと（差分は追加分のみ）を確認しました。
- jtalkDriver.py のPython構文チェックを通過しました。
- 完成した .nvda-addon のZIP整合性を確認しました。
- 実機確認：V5は作者の環境で確認済み。V6〜V8は未確認です（README参照）。

## 実機確認の結果（2026-11-16）

感情ラインナップ版を作者の実機で確認しました。

- takumi 全4種（V5〜V8）：動作良好。
- mei の感情4種（V9〜V12）：全員、動作良好。
- slt（V13）：超高速の喋りと「バリバリ」という雑音が聞こえ、音声とは言えない状態でした。英語ラベルで学習された音声を日本語ラベルで駆動する限界と判断します。

## 追補：感情ラインナップ版（2026-11-16）

Takumi全パターン版（V1〜V8）を土台に、Meiの感情音声と英語音声SLTを追加したビルドです。成果物は `nvdajp-jtalk-2026.3.1jp-emotion-lineup.nvda-addon` です。

### 追加した音声ファイル

- `synthDrivers/jtalk/mei_emotions/` フォルダを新設し、MMDAgent_Example-1.8 の Mei 感情音声4つ（mei_happy / mei_angry / mei_sad / mei_bashful、各2,221,416バイト）と、配布物のCOPYRIGHT.txt・README.txtを入れました。
  - 配置上の注意：既存のMei（V2）は `mei/mei_happy.htsvoice` を指していますが、同梱ファイル（862,503バイト）はMMDAgent版（2,221,416バイト）とは別物です。`mei/` に入れると同梱ファイルや同梱のCOPYRIGHT.txt・README.txtを上書きしてV2の声が変わるため、別フォルダにしました。V2は無変更です。
- `synthDrivers/jtalk/slt/` フォルダを新設し、cmu_us_arctic_slt.htsvoice（1,515,783バイト）と配布物のCOPYRIGHT.txtを入れました。
- クレジットとして `CREDIT-mei-emotions.txt` と `CREDIT-slt.txt` を追加しました（本リポジトリでは `source/` に収録）。

### ドライバーの声一覧への追加

`_jtalk_voices` に V9〜V13 の5エントリを追加しました。

- V9: mei_happy
- V10: mei_angry
- V11: mei_sad
- V12: mei_bashful
- V13: slt（言語は "en" として登録）

音声条件は各ファイルの埋め込みヘッダーから実測し、5ファイルとも SAMPLING_FREQUENCY 48000 / FRAME_PERIOD 240 / ALPHA 0.55 でした。SLTのヘッダーも48000でした（16000ではありません）。その他のパラメータは既存のMei（V2）を起点にしました（lf0_base 5.9、pitch_bias -25、inflection_bias -10、speaker_attenuation 0.8、beta 0.00）。デフォルトの声（V4）は変更していません。

改変後のドライバー全文（V1〜V13）は `source/jtalkDriver.py` に収録しています（本節の追補にあわせて差し替え済み）。

### ライセンス

- Mei：HTS Voice "Mei"、Copyright (c) 2009-2018 Nagoya Institute of Technology、CC BY 3.0。
- SLT：HTS Voice "CMU ARCTIC SLT"。音声データベース部分は Carnegie Mellon University（Copyright (c) 2003）の許諾条件、HTS Voice部分は HTS Working Group／Nagoya Institute of Technology ほかの CC BY 3.0。

### SLTについての注意

SLTは英語のフルコンテキストラベルで学習された英語音声で、Open JTalkが生成する日本語ラベルとは一致しません。そのため日本語を正しく発音できない、あるいは音が出ない可能性があります。実験的な英語話者としての収録であり、動作は保証しません。

### 検証（ビルド時）

- 土台（Takumi全パターン版）の57件はすべて残り、追加は意図した10件のみ（合計67件）。内容が変わったファイルは jtalkDriver.py のみ（CRC比較）。
- jtalkDriver.py のPython構文チェックを通過しました。
- 完成した .nvda-addon のZIP整合性を確認しました。manifest.ini あり。
- 実機確認：V9〜V13は未確認です。
