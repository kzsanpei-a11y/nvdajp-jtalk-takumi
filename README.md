# nvdajp-jtalk-takumi

NVDA日本語版のJTalkアドオンに、フリーの男性音声「Takumi」を追加したビルドです。

公式の `nvdajp-jtalk-2026.3.1jp` アドオンを土台に、音声を8つ追加しました。既存の声とデフォルト設定は変更していません。

## 追加される声

| ID | 声 | 内容 |
|----|----|------|
| V5 | takumi | Takumi（通常） |
| V6 | takumi_happy | Takumi（嬉しい） |
| V7 | takumi_angry | Takumi（怒った） |
| V8 | takumi_sad | Takumi（悲しい） |
| V9 | mei_happy | Mei（嬉しい） |
| V10 | mei_angry | Mei（怒った） |
| V11 | mei_sad | Mei（悲しい） |
| V12 | mei_bashful | Mei（照れ） |

既存の声（V1: m001、V2: mei、V3: lite、V4: tohoku-f01）はそのまま残ります。デフォルトはV4（tohoku-f01）のままです。

## ダウンロードとインストール

1. 次のリンク（Googleドライブ）から `nvdajp-jtalk-2026.3.1jp-takumi-mei.nvda-addon` をダウンロードします。

https://drive.google.com/file/d/17oSkjH4ddbhkHyrBA7dLf6QsORut_iCO/view
2. NVDAのアドオンストア、または「ツール」→「アドオンをインストール」から、そのファイルを開いてインストールします。
3. NVDAの設定で音声合成エンジンにJTalkを選び、声の一覧から takumi 系の声を選びます。

## 動作確認の状況

- takumi 全4種（V5〜V8）と mei の感情4種（V9〜V12）は、作者の実機環境（NVDA日本語版ポータブル版）で動作を確認しています。動作は軽快です。
- 英語音声SLTも実験的に組み込んで試しましたが、実機では超高速の喋りと「バリバリ」という雑音になるだけで音声として成立しなかったため、公開版には含めていません。英語のラベルで学習された音声を日本語のラベルで駆動することの限界とみられます。

## ライセンスとクレジット

- このアドオンの土台であるNVDA日本語版およびJTalkアドオンは、GNU General Public Licenseのもとで配布されているソフトウェアです。本リポジトリには、改変したドライバー（`source/jtalkDriver.py`）を収録しています。
- 追加した音声「Takumi」と「Mei」は、名古屋工業大学（MMDAgentプロジェクトチーム）の著作物で、Creative Commons 表示 3.0（CC BY 3.0）で提供されています。クレジット表記はアドオン内および `source/` フォルダに収録しています。
- 各音声ファイルは、MMDAgent公式配布物（MMDAgent_Example-1.8）から取得しました。

## 変更点

詳しくは [CHANGES.md](CHANGES.md) をご覧ください。

## 作者

星野和寿（つどいグループ）
