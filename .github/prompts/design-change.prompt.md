---
name: Design Change
description: 変更仕様書を入力として、設計成果物を標準化された手順で作成する
argument-hint: 変更仕様書のMarkdownファイルを添付またはパスで指定してください
agent: "Change Designer"
---

対象変更仕様書: `${input:changeSpecPath}`

上記で指定された変更仕様書を原本として、Change Designer の設計作業を実施してください。

## 最優先: 入力確認ゲート

作業を開始する前に、`${input:changeSpecPath}` に値が入力され、対象の Markdown ファイルが指定されているかだけを確認してください。

- 値が入力されている場合だけ、以下の作業へ進む。
- 値が入力されていない場合は、ファイル検索・既存ファイルの読み取り・設計判断・成果物作成を一切行わず、次の一文だけを返して停止する。

> 対象の変更仕様書 Markdown ファイルを添付するか、ワークスペース相対パスで指定してください。

入力値をワークスペース内から推測したり、過去の会話で使ったファイルを再利用したりしてはならない。

## 入力

- 変更仕様書は、`changeSpecPath` に入力された Markdown ファイルを使用する。
- `changeSpecPath` が空の場合は、入力確認ゲートの指示だけを実行する。
- 変更仕様書の内容は変更しない。

## 作業

1. 変更要求を Requirement に分解する。
2. Requirement ごとに `Change Impact Analyzer` へ既存設計、ソースコード、ユニットテストの事実調査を委譲し、返却結果を影響分析へ統合する。
3. 変更仕様書と同じ Change Package に `impact-analysis.md` を作成する。
4. 同じ Change Package に `traceability.md` を作成する。
5. 同じ Change Package に `implementation-plan.md` を作成する。
6. 影響分析に基づき、必要な既存 Markdown 設計書だけを更新する。
7. 不明点は推測で確定せず、`TBD`、Open Questions、または `Needs Clarification` として記録する。
8. Requirement、設計、ソース、ユニットテストの対応を成果物間で一致させる。

## 禁止事項

- `src/`、`include/`、`test/` 配下を変更しない。
- ソースコードおよびユニットテストを実装・変更しない。
- 変更仕様に存在しない要求を追加しない。
- `Change Impact Analyzer` 以外の Subagent を使用しない。
- Skill、Terminal、Shell を使用しない。

作業完了後、変更した Markdown ファイル、Open Questions、Risks、重要な設計判断を提示し、次の文言で停止してください。

> Design Review Gate に到達しました。実装は開始していません。
