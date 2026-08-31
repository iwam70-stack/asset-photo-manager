# asset-photo-manager

備品シールと備品全体をスマートフォンで撮影し、備品番号と写真を対応付けてGoogle Driveへ保存するためのアプリ開発プロジェクトです。

## 概要

備品シールを撮影し、OCRで抽出した備品番号候補を利用者が確認して、必要に応じて手修正します。
備品番号の確定後に備品全体を撮影し、シール写真と全体写真を1件の撮影ジョブとして管理します。

撮影データはアップロード前に端末内へ保存し、完成済みの未送信ジョブを保持・復旧できる構成とします。
撮影処理とアップロード処理を分離し、写真はGoogle Driveへ保存します。

FlutterおよびDartで開発し、初期開発ではAndroidを優先します。

## 現在の状態

現在は開発文書の初期整備段階です。要件、設計、判断記録、進捗、テスト計画の初期版は作成済みです。

Flutterプロジェクト、アプリコード、およびテストコードはまだ作成していません。
そのため、アプリはまだ実行・利用できる状態ではなく、テスト、静的解析、ビルド、実機確認も未実施です。
主要仕様と技術選定には未確定事項が残っています。

最新の現在状態は[docs/progress.md](docs/progress.md)を参照してください。

## 基本的な処理の流れ

1. 備品シールを撮影する。
2. OCR結果を確認し、必要に応じて修正する。
3. 備品番号を確定する。
4. 備品全体写真を撮影する。
5. 写真と備品番号を撮影ジョブとして端末内へ保存する。
6. 完成済みジョブをGoogle Driveへ送信する。
7. オフラインや送信失敗時は未送信ジョブを保持し、後で再送する。

## 文書

| 文書 | 役割 |
| --- | --- |
| [AGENTS.md](AGENTS.md) | Codexが守る作業規則 |
| [docs/requirements.md](docs/requirements.md) | 機能要件、非機能要件、制約、未確定事項 |
| [docs/design.md](docs/design.md) | 現在採用しているシステム設計 |
| [docs/decisions.md](docs/decisions.md) | 重要な判断の結論、理由、代替案 |
| [docs/progress.md](docs/progress.md) | 現在の開発状態、問題、次の作業 |
| [docs/test-plan.md](docs/test-plan.md) | テスト対象、環境、異常系、完了方針 |

## リポジトリ構成

```text
asset-photo-manager/
├── AGENTS.md
├── README.md
└── docs/
    ├── decisions.md
    ├── design.md
    ├── progress.md
    ├── requirements.md
    └── test-plan.md
```

Flutterプロジェクトは、将来リポジトリルートの`app/`以下へ作成する計画です。

## 開発上の注意

- 作業前に[AGENTS.md](AGENTS.md)を読む。
- 未確定仕様を推測で実装しない。
- 認証情報、秘密鍵、実在する備品番号、実際の備品写真、および個人情報をGitへ含めない。
- サービスアカウント秘密鍵をアプリへ埋め込まない。
- 実行していないテストやビルドを成功扱いにしない。
- 重要な判断は[docs/decisions.md](docs/decisions.md)、現在状態は[docs/progress.md](docs/progress.md)へ反映する。

## ライセンス

未定。
