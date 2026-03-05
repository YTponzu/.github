# Template C: Node.js Backend

## 向いているプロジェクト

- APIサーバー・マイクロサービス
- バッチ処理・定期実行スクリプト
- CLIツール
- フロントエンドなし、または別リポジトリで管理

## 技術スタック

| 役割 | 技術 |
|------|------|
| ランタイム | Node.js |
| フレームワーク | Hono（軽量API）または素のNode.js |
| バリデーション | Zod |
| DB（必要なら） | Convex / PostgreSQL / SQLite |
| デプロイ | Railway / Fly.io / VPS |

## ディレクトリ構成

```
src/
├── index.ts                # エントリーポイント
├── routes/                 # ルーティング定義
│   └── [resource].ts
├── handlers/               # リクエストハンドラー
│   └── [resource]/
│       ├── get.ts
│       ├── create.ts
│       └── update.ts
├── services/               # ビジネスロジック
│   └── [resource].ts
├── repositories/           # DB操作の抽象化
│   └── [resource].ts
├── schemas/                # Zodバリデーションスキーマ
│   └── [resource].ts
└── lib/                    # 汎用ユーティリティ
    ├── db.ts               # DB接続
    └── errors.ts           # エラー定義

tests/                      # テスト
└── [resource].test.ts
```

## ルール

- `handlers/` はリクエスト/レスポンスの変換のみ（ロジックは `services/` へ）
- `services/` はDB操作を直接書かない（`repositories/` 経由）
- 全ての入力値は `schemas/` の Zod スキーマでバリデーション
- エラーは `lib/errors.ts` の型を使って統一的に扱う

## 環境変数

```env
PORT=3000
DATABASE_URL=xxx
API_KEY=xxx
```
