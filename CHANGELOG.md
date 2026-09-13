# 変更履歴（Changelog）

このファイルには、本プロジェクトにおけるすべての重要な変更を記録しています。

本形式は [Keep a Changelog](https://keepachangelog.com/ja/1.0.0/) に基づいており、
[セマンティック バージョニング](https://semver.org/lang/ja/) に従って運用しています。

---

## [1.0.0] - 2026-09-13

### 追加
- **カスタムエージェント**
  - 設計フェーズ専門カスタムエージェント `Change Designer`（`.github/agents/change-designer.agent.md`）
  - ツール境界（`read`, `search`, `edit` かつ Markdown ファイル限定、ソースコード編集禁止）の定義
  - 人間によるレビューと承認を必須とする Design Review Gate
- **変更管理パッケージのサンプル（CHG-0001）**
  - 変更仕様書原本 `changes/CHG-0001/change-spec.md`（ユーザー名空文字検証と例外契約）
- **詳細設計ドキュメント**
  - `sampleapp` モジュールの詳細設計書 `docs/sampleapp-specs/sampleapp-design.md`（3層アーキテクチャ、API契約、エラー境界、テスト設計）
