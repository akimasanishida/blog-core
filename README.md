# blog-core

Next.js 製マークダウンブログ基盤

## プロジェクト構成

### 基本構成

- pnpm
- next15 (AppRouter)
- firebase

### 使用ライブラリ

- next
- shadcn

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
  - categories/  # `/categories`
  - forget-password/  # `/forget-password`
  - login/  # `/login`
  - media/[...path]  # `/media`
  - post/[slug]  # `/post`
  - search/  # `/search`
  - set-password/  # `/set-password`
- components/
  - ui/  # shadcn により追加
- lib
  - utils.ts  # shadcn により追加

### URL

- `/search`
  - `q`：検索クエリ

## 実行

```bash
pnpm dev
```