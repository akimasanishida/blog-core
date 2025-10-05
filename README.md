# blog-core

Next.js 製マークダウンブログ基盤

## プロジェクト構成

### 基本構成

- pnpm
- next15 (AppRouter)
- firebase

### 使用ライブラリ

- next

#### UI

- shadcn: UI
- @phosphor-icons/react: アイコン
- lucide-react: アイコン（補助）

#### Markdown レンダリング



### ディレクトリ構成

```
.
├── public  # 基本的に空
├── README.md
├── src
│   ├── app
│   ├── components
│   ├── lib
│   └── types
└── tsconfig.json
```

```
app/
├── actions/                # server actions
├── admin/                  # 管理者専用。記事一覧を表示
│   ├── post/               # 記事作成・編集
│   │   └── preview/        # 編集中の記事のプレビュー
│   ├── media/              # 画像管理（将来的に動画・音声対応）
│   └── settings/           # サイト設定
├── archives/               # アーカイブ年月一覧（表示形式未定）
│   └── [year]/             # 各年の投稿一覧
│       └── [month]/        # 各年月の投稿一覧
├── category/               # カテゴリー一覧ページ
│   └── [category]/         # 各カテゴリの記事一覧
├── login/                  # ログインページ
├── media/[...path]/        # Storage との疎通
├── post/[slug]/            # 記事閲覧
└── search/                 # 記事検索

components/
└── ui/                     # shadcn により追加

lib/
└── utils.ts                # shadcn により追加
```

### URL

- `login`：ログインページ
- `/search`
  - `q`：検索クエリ
- `admin`：ログイン済みの場合のみアクセス可能

### 機能

#### アカウント機能

アカウント所有者は管理者機能を持つ

| ロール | 通常ページ | 管理者機能（`/admin` 以下） |
| --- | --- | --- |
| 管理者（アカウント所持） | :o: | :o: |
| ゲストユーザ | :o: | :x: |

- 管理者機能
  - 記事の作成・編集・削除
  - メディアの投稿・削除
- アカウント機能
  - ログイン（現時点では GitHub の連携のみ）
  - 非ログインユーザをログインページへ遷移

#### Firebase 連携

- データベース疎通
- ストレージ疎通
- 認証

#### Markdown レンダリング

Markdown を HTML へレンダリングする。

- GitHub Flavored Markdown
- KaTeX
- prism.js によるコードブロックのシンタックスハイライト

## 実行

```bash
pnpm dev
```