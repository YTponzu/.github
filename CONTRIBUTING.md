# Contributing Guide（共通）

YTponzu の全リポジトリに適用される開発ルールです。
各プロジェクトに固有のルールがある場合は、そのリポジトリの `CONTRIBUTING.md` を参照してください。

## 基本方針

- コードはシンプルに保つ
- 変更は小さく、レビューしやすい単位で
- ドキュメントはコードと一緒に更新する
- 壊れたまま `main` に入れない

## ドキュメント

| ファイル | 内容 |
|----------|------|
| [docs/GITHUB.md](docs/GITHUB.md) | ブランチ戦略・コミット規約・PRルール |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | アーキテクチャ選定ガイド・テンプレート |
| [docs/DESIGN.md](docs/DESIGN.md) | デザインツール・Figma運用・Storybook判断基準 |
| [docs/TESTING.md](docs/TESTING.md) | テスト戦略・TDD・フレームワーク選定基準 |
| [docs/AGENTS.md](docs/AGENTS.md) | エージェント共有ガイド・AGENTS.mdテンプレート |

## 開発フロー

1. `main` から作業ブランチを切る
2. 変更を加えてコミット（[Conventional Commits](docs/GITHUB.md) 形式）
3. PR を作成して `main` にマージ
4. ブランチを削除する
