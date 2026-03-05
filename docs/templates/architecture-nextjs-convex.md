# Template A: Next.js + Convex

## 向いているプロジェクト

- リアルタイム同期が必要（ダッシュボード・チャット・コラボツール等）
- スキーマ定義からAPIまで一元管理したい
- バックエンドをできるだけ書きたくない

## 技術スタック

| 役割 | 技術 |
|------|------|
| フレームワーク | Next.js 15（App Router） |
| バックエンド・DB | Convex |
| スタイリング | Tailwind CSS |
| デプロイ | Vercel（フロント）+ Convex Cloud |

## ディレクトリ構成

```
src/
├── app/                    # ルーティングのみ（ページは薄く保つ）
│   ├── layout.tsx
│   ├── page.tsx
│   └── [feature]/
│       └── page.tsx        # features/ の View を呼ぶだけ
├── features/               # 機能単位のまとまり
│   └── [feature]/
│       ├── components/     # この機能専用のUIコンポーネント
│       ├── hooks/          # Convexクエリ・ミューテーションのラッパー
│       └── types.ts        # この機能の型定義
├── components/             # 共通UIコンポーネント（特定機能に依存しない）
└── lib/                    # 汎用ユーティリティ・定数

convex/                     # バックエンド
├── schema.ts               # DBスキーマ定義
├── [feature].ts            # クエリ・ミューテーション
└── _generated/             # 自動生成（編集しない）
```

## ルール

- `app/` のページコンポーネントは100行以内を目安に保つ
- Convexのクエリ・ミューテーションは `features/xxx/hooks/` でラップして使う
- `components/` には特定の機能に依存するコンポーネントを置かない
- `convex/schema.ts` の変更は影響範囲が広いため慎重に行う
- `convex/_generated/` はgitignoreしない（Vercelビルドで必要）

## 環境変数

```env
NEXT_PUBLIC_CONVEX_URL=https://xxx.convex.cloud
CONVEX_DEPLOY_KEY=xxx   # Vercel本番環境のみ
```
