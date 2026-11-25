# リリースノート

本ドキュメントは、NVDA日本語版向けOpen JTalkアドオンの改変版 `nvdajp-jtalk-2026.3.1jp-takumi-mei.nvda-addon` の初回リリースノートです。

## 概要

公式リリースの `nvdajp-jtalk-2026.3.1jp.nvda-addon`（NVDA日本語版 2026.3.1jp のJTalkアドオン）を土台とし、追加の音声として Takumi の4種および Mei の感情音声4種を追加した、全12声（V1〜V12）構成のアドオンです。

なお、開発段階では英語音声SLT（V13）の収録を実験的に試みましたが、実機確認において超高速の喋りと「バリバリ」という雑音になるだけで音声として成立しなかったため、今回の公開版からは除外しています。
デフォルトの声（V4）は土台アドオンから変更していません。

## 収録する声の一覧

本アドオンには以下の全12種類の声が収録されています。

- **V1〜V4：土台アドオンの既存音声**
  - V1: m001
  - V2: mei（土台アドオンに同梱の `mei/mei_happy.htsvoice`）
  - V3: lite
  - V4: tohoku-f01（デフォルト）
- **V5〜V8：Takumi（新規追加）**
  - V5: takumi（通常音声 / `takumi_normal.htsvoice`）
  - V6: takumi_happy（嬉しい）
  - V7: takumi_angry（怒った）
  - V8: takumi_sad（悲しい）
- **V9〜V12：Mei 感情音声（MMDAgent版・新規追加）**
  - V9: mei_happy（嬉しい）
  - V10: mei_angry（怒った）
  - V11: mei_sad（悲しい）
  - V12: mei_bashful（照れ）

※既存のMei（V2）とV9〜V12は元ファイルが異なるため、上書きを避けて `mei_emotions/` フォルダに新規配置しています。V2の音声に変更はありません。

## インストール方法

1. Googleドライブから `nvdajp-jtalk-2026.3.1jp-takumi-mei.nvda-addon` をダウンロードします（リンクは README をご覧ください）。
2. NVDAが起動している状態でダウンロードしたファイルを直接開くか、NVDAのアドオンストア、または「ツール」→「アドオンをインストール」から、そのファイルを開いてインストールします。
3. NVDAの指示に従って再起動します。
4. NVDAの「設定」→「音声」設定項目（シンセサイザーは「Open JTalk」）を開き、「声」の選択欄から追加された音声（V5〜V12）を選択します。

## 動作確認の状況

- **ビルド時の検証**
  - 土台アドオンの収録ファイル一覧と比較し、ファイルの欠落がないこと（差分は意図した追加ファイルのみであること）を確認済みです。
  - `jtalkDriver.py` のPython構文チェックを通過しています。
  - 生成された `.nvda-addon` ファイルのZIP整合性および `manifest.ini` の存在を確認済みです。
- **実機での動作確認**
  - 作者の実機環境において動作確認を行いました。
  - Takumi 全4種（V5〜V8）：動作良好。
  - Mei の感情4種（V9〜V12）：動作良好。
  - （実験的に導入した英語音声SLTは実機で音声として成立しなかったため、公開版から取り除かれています）

## ライセンスとクレジット

- **NVDA日本語版およびJTalkアドオン（土台部分）**
  - GNU General Public License (GPL)
- **追加音声（Takumi および Mei）**
  - 名古屋工業大学（MMDAgentプロジェクトチーム）の著作物です。
  - ライセンス：Creative Commons Attribution 3.0 Unported (CC BY 3.0)
  - HTS Voice "Takumi": Copyright (c) 2011-2015 Nagoya Institute of Technology
  - HTS Voice "Mei": Copyright (c) 2009-2018 Nagoya Institute of Technology
  - パッケージ内およびリポジトリ内に `CREDIT-takumi.txt`、`CREDIT-mei-emotions.txt`、および各音声に付属の `COPYRIGHT.txt`、`README.txt` を収録しています。