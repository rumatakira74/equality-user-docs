# Equality Project — ユーザー向けドキュメント

ロシア語の原文：[README.md](../README.md)。

**Equality Project** は、コミュニティがメンバーの電話上に**自分たちの隔離されたトラストネットワーク**を立ち上げるためのプラットフォームです：サーバーなし、管理者なし、運用コストなし。

**DOI：** [10.5281/zenodo.23558900](https://doi.org/10.5281/zenodo.23558900)

> **ステータス：テスト版（pre-release）。** アプリはエミュレータ上のテストネットワークで完全に検証済みです。実機での検証と最初のパイロットはこれからです。ドキュメントは、仕様 v9.16 / protocol_version 3 に従った製品の動作を記述しています（ガーディアンの再選出 `update_guardians` を含む：48 時間のウィンドウ、発効した交代は 150 回まで；第 8 のシナリオ — サブスクリプション型リソース：周期クォータと失効を伴うサブスクリプション型ネットワーク (recurring)）。

> **言語。** ドキュメントはロシア語（原文、`docs/`）と翻訳で利用できます：
> [このディレクトリ](.) — 日本語。アプリのインターフェース言語 —
> ru, en, es, pt, zh, fr, de, it, ja（メインリポジトリの `app/lib/l10n`）。

© 2026 Kirill Lapchinsky · rumatakira74@gmail.com · Telegram [@rumatakira](https://t.me/rumatakira)

## 目次

1. [プラットフォームについて](docs/01-about.md) — これは何か、誰のためのものか、8 つのシナリオ、役割
2. [はじめに](docs/02-getting-started.md) — インストール、ウォレットの作成、保証、アクセス
3. [日常の操作](docs/03-operations.md) — 発行、送金、手数料、デマレージ、復旧
4. [所有者のセキュリティ](docs/04-security.md) — PIN と生体認証、脅迫 PIN、保護の限界
5. [よくある質問と用語集](docs/05-faq-glossary.md)

## プロジェクトの他のリポジトリ

- [equality-trust-networks](https://github.com/rumatakira74/equality-trust-networks) — プラットフォームのソースコードと仕様
- [equality-programming-docs](https://github.com/rumatakira74/equality-programming-docs) — プログラマー向けドキュメント
- [equality-anti-farm-simulation](https://github.com/rumatakira74/equality-anti-farm-simulation) — ファーム経済のモデル（パラメータの根拠）

## 免責事項

プロジェクトは予備リリースのステータスにあります。保証と責任の限界は [DISCLAIMER.md](DISCLAIMER.md)（日本語と英語）に記述されています。

## ライセンス

ソースコードは**非営利利用**のために公開されています。営利利用と営利目的の派生物 — 有料ライセンスの下で（条件は仕様のセクション 16）。

ライセンス本文：[LICENSE](../LICENSE)（ロシア語の原文、法的に優先）· [LICENSE-ENG.md](../LICENSE-ENG.md)（非公式の英語訳）。
