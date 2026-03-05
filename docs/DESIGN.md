# デザインガイド（共通）

## ツール選定

| ツール | 用途 | 導入タイミング |
|--------|------|--------------|
| **Figma** | UI設計・デザインカンプ | 全プロジェクト必須 |
| **Figma MCP** | エージェントによるFigma参照・実装 | Figmaを使うプロジェクト全て |
| **Storybook** | コンポーネントカタログ・ドキュメント | 共通コンポーネントが10個以上 or チーム開発時 |

---

## デザインフロー

```
1. Figmaで設計
        ↓
2. ぽんずがデザインをレビュー・承認
        ↓
3. エージェントがFigma MCPでデザインを参照して実装
        ↓
4. 実装結果をぽんずが確認
        ↓
5.（規模が大きくなったら）Storybookにコンポーネントを登録
```

---

## Figma 運用ルール

### ファイル構成

```
Figma/
└── [プロジェクト名]/
    ├── 🎨 Design System   # カラー・タイポグラフィ・コンポーネント定義
    ├── 📐 Wireframes      # ワイヤーフレーム・情報設計
    └── 🖥 UI Design       # 実装用デザインカンプ
```

### デザインカンプを作るタイミング

| 作る | 作らない |
|------|---------|
| 新しいページ・画面の追加 | 既存コンポーネントの色変更 |
| 複雑なUIの変更 | テキストの修正 |
| ユーザーに見える大きな変更 | バグ修正 |

### デザイントークン

Figmaの変数（Variables）とコードのCSS変数を対応させる。

| Figma変数 | CSS変数 |
|-----------|---------|
| `color/background` | `--background` |
| `color/foreground` | `--foreground` |
| `color/primary` | `--primary` |
| `color/accent` | `--accent` |
| `color/success` | `--success` |
| `color/warning` | `--warning` |
| `color/error` | `--error` |

---

## Figma MCP セットアップ

### 必要なもの

- Figma アカウント（Pro プラン）
- Figma MCP サーバー
- プロジェクトの `.env.local` に Figma アクセストークンを設定

### 環境変数

```env
FIGMA_ACCESS_TOKEN=xxx   # Figma → Settings → Personal access tokens
```

### 使い方

エージェントへの指示例：

```
Figmaのデザイン（[ファイルURL]）を参照して、
Agentsページのカードコンポーネントを実装してください。
```

---

## Storybook 導入判断基準

以下のいずれかに当てはまったら導入する：

- [ ] 共通コンポーネントが10個以上になった
- [ ] チームメンバーが増えた
- [ ] コンポーネントの仕様を口頭・文章で説明するのが難しくなってきた
- [ ] デザイナーとエンジニアの認識がずれることが増えてきた

### 導入時のセットアップ

```bash
npx storybook@latest init
```

各プロジェクトの `docs/DESIGN.md` に Storybook の URL を記載する。

---

## 各プロジェクトの DESIGN.md に書くこと

プロジェクト固有の `docs/DESIGN.md` には以下を記載する：

```markdown
## 使用ツール
- Figma: [ファイルURL]
- Storybook: [URL]（導入済みの場合）

## デザイントークン
（プロジェクト固有のカラー・スペーシング定義）

## コンポーネントルール
（プロジェクト固有のUIルール）
```
