# Template B: Next.js + REST API

## 向いているプロジェクト

- 外部APIと連携するWebアプリ
- Next.js の API Routes（BFF）でデータ加工したい
- リアルタイム同期は不要

## 技術スタック

| 役割 | 技術 |
|------|------|
| フレームワーク | Next.js 15（App Router） |
| API層 | Next.js Route Handlers（BFF） |
| スタイリング | Tailwind CSS |
| バリデーション | Zod |
| デプロイ | Vercel |

## ディレクトリ構成

```
src/
├── app/                    # ルーティング
│   ├── layout.tsx
│   ├── page.tsx
│   ├── api/                # Route Handlers（BFF）
│   │   └── [resource]/
│   │       └── route.ts
│   └── [feature]/
│       └── page.tsx
├── features/               # 機能単位のまとまり
│   └── [feature]/
│       ├── components/     # この機能専用のUIコンポーネント
│       ├── hooks/          # データフェッチのラッパー（SWR / fetch）
│       ├── actions.ts      # Server Actions
│       └── types.ts        # 型定義・Zodスキーマ
├── components/             # 共通UIコンポーネント
└── lib/                    # 汎用ユーティリティ・APIクライアント
    ├── api.ts              # fetchラッパー
    └── utils.ts
```

## ルール

- 外部APIへの直接呼び出しはクライアントから行わない（必ずBFF経由）
- `features/xxx/types.ts` に Zod スキーマを定義し、APIレスポンスをバリデーションする
- Server Actions は `features/xxx/actions.ts` にまとめる
- `lib/api.ts` にfetchの共通ラッパーを置き、エラーハンドリングを一元化する

## 環境変数

```env
EXTERNAL_API_URL=https://api.example.com
EXTERNAL_API_KEY=xxx    # サーバーサイドのみ（NEXT_PUBLIC_ をつけない）
```
