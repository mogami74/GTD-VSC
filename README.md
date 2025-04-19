# GTD-VSC

## 利用に必要な前提条件

- VisualStudioCode の基本的な使い方がわかる
- ターミナルの基本的な使い方がわかる
- インターネット環境がある

## 導入方法

github から ソースコードを Clone してください。

## 初期設定


## 基本的な流れ

VSCodeのエージェントモードで利用することを前提にしています。

- `GTD/inbox.md` にタスクを収集する。
- Copilotチャットでエージェントモードを選択。`process GTD`と入力すると、inbox内のタスクに対して、GTDのプロセスを実行します。AIが「アクション可能か？」などの質問の回答案を提案してきます。賛成であれば、そのまま分類されます。別の分類がよければチャットでそのように伝えます。
- 分類されたタスクは`GTD/inbox.md`から削除され、各分類に応じたファイルに移動されます。
- 分類されたタスクは、`GTD/actions.md`、`GTD/projects.md`、`GTD/waiting.md`、`GTD/calendar.md`、`GTD/someday_maybe.md`、`GTD/reference.md`に格納されます。
- 完了したタスクは`GTD/archive.md`に格納されます。

## コマンド

### `process GTD`

エージェントモードに`process GTD`や「GTDを処理して」と入力すると、GTDのプロセスを実行します。

## 構成

### `.github/copilot-instructions.md`

すべての動作はこのファイルで規定されています。
現状英語で記載していますが、日本語で追記することも可能です。
動作を調整したい時はこのファイルを修正してください。

### `GTD`

- `GTD/context-list.md`
  - コンテクスト（タスクを実行できる状態）を定義する。
- `GTD/inbox.md`
  - タスクを収集する。
  - 1行1タスクで、箇条書きで記載する。
- `GTD/archive.md`
  - 完了したタスクを格納する
- `GTD/actions.md`
- `GTD/calendar.md`
- `GTD/projects.md`
- `GTD/reference.md`
- `GTD/someday_maybe.md`
- `GTD/waiting.md`

## 制限事項


## Tips

