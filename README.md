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

- app/
  - actions/  # server actions
  - admin/  # `/admin`
  - archives/  # `/archives`
    - [year]  # 各年のアーカイブ一覧
      - [month]  # 各月のアーカイブ一覧
  - category/  # `/category`
    - [category]  # 各カテゴリの一覧
  - forget-password/  # `/forget-password`
  - login/  # `/login`
  - media/[...path]  # `/media` ストレージとの疎通
  - post/[slug]  # `/post`
  - search/  # `/search`
  - set-password/  # `/set-password`
- components/
  - ui/  # shadcn により追加
- lib
  - utils.ts  # shadcn により追加

### URL

- `login`：ログインページ。ヘッダ・フッタ非表示
- `/search`
  - `q`：検索クエリ

### 機能

#### アカウント機能

| ロール | 閲覧（公開時） | 閲覧（非公開時） | 管理者機能 |
| --- | --- | --- | --- |
| 管理者 | :o: | :o: | :o: |
| アカウントユーザ | :o: | :o: | :x: |
| ゲストユーザ | :o: | :x: | :x: |

- 管理者機能
  - 記事の作成・編集・削除
  - メディアの投稿・削除
  - ユーザの招待・削除
- アカウント機能
  - ログイン
  - パスワードの設定・再設定

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