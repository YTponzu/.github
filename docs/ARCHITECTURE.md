# アーキテクチャ選定ガイド

各プロジェクトのアーキテクチャは、このガイドに従って選定し、
プロジェクト内の `docs/ARCHITECTURE.md` に記録する。

---

## 選定フロー

以下の質問に答えてテンプレートを選ぶ。

### Q1. フロントエンドはあるか？

- **Yes** → Q2 へ
- **No（APIのみ）** → [Template C: Node.js Backend](templates/architecture-node-backend.md)

### Q2. リアルタイム同期・サブスクリプションが必要か？

- **Yes** → [Template A: Next.js + Convex](templates/architecture-nextjs-convex.md)
- **No** → Q3 へ

### Q3. バックエンドは外部API or 自前REST APIか？

- **外部API or BFF構成** → [Template B: Next.js + REST API](templates/architecture-nextjs-rest.md)
- **自前バックエンドも作る** → Template A or C を組み合わせて検討

---

## 選定時に記録すること

プロジェクトの `docs/ARCHITECTURE.md` に以下を書く：

```markdown
## 選定理由
なぜこのアーキテクチャを選んだか（1〜3行）

## ベーステンプレート
どのテンプレートを使ったか（リンク）

## カスタマイズ点
テンプレートから変えた点があれば記載
```

---

## テンプレート一覧

| テンプレート | 用途 |
|-------------|------|
| [A: Next.js + Convex](templates/architecture-nextjs-convex.md) | リアルタイム同期が必要なWebアプリ |
| [B: Next.js + REST API](templates/architecture-nextjs-rest.md) | 外部API連携・BFF構成のWebアプリ |
| [C: Node.js Backend](templates/architecture-node-backend.md) | APIサーバー・バッチ・CLIツール |
