# CLAUDE.md

このファイルは、このリポジトリでコードを操作する際に Claude Code (claude.ai/code) に指針を提供します。

## プロジェクト概要

このワークスペースには `cursor-example/` が含まれており、**Next.js 14+、React 19、TypeScript、Tailwind CSS** で構築された静的ブログです。ブログ記事は `/_posts` フォルダに Markdown ファイルとして保存され、ビルド時に `remark` と `gray-matter` を使用して HTML に変換されます。

## 開発開始

### 依存をインストール
```bash
cd cursor-example
npm install
```

### 開発サーバーを起動
```bash
npm run dev
```
`http://localhost:3000` で動作し、Turbopack で高速リフレッシュを実現します。

### 本番用にビルド
```bash
npm run build
npm start
```

## プロジェクト構成

### 主要ディレクトリ
- **`cursor-example/`** — メイン Next.js ブログアプリケーション
  - **`app/`** — Next.js App Router（ページとレイアウト）
  - **`components/`** — React コンポーネント
  - **`_posts/`** — Markdown ブログ記事ファイル（フロントマター + 本文）
  - **`public/`** — 静的アセット
  - **`styles/`** — グローバル CSS と Tailwind 設定

### 静的生成と Markdown 処理

- `_posts/*.md` のブログ記事は以下を使用して処理されます：
  - **`gray-matter`** — フロントマター（タイトル、日付、著者など）と本文を抽出
  - **`remark` + `remark-html`** — Markdown を HTML に変換
- 記事はビルド時に静的ページとしてレンダリングされます（サーバーサイドレンダリングなし）
- `_posts/` に新しい `.md` ファイルを追加すると、自動的に新しい記事が作成されます

## 技術スタック

| レイヤー | 技術 |
|---------|------|
| ランタイム | Node.js 18+ |
| フレームワーク | Next.js（最新、App Router） |
| UI | React 19 |
| 言語 | TypeScript 5.5+ |
| スタイリング | Tailwind CSS 3.4 + PostCSS + Autoprefixer |
| Markdown | remark + remark-html + gray-matter |
| ビルド | Next.js with Turbopack |

## 設定ファイル

- **`package.json`** — 依存とビルドスクリプト
- **`tsconfig.json`** — TypeScript 設定
- **`tailwind.config.ts`** — Tailwind CSS カスタマイズ
- **`postcss.config.js`** — PostCSS プラグイン（Tailwind、Autoprefixer）
- **`next.config.js`** （存在する場合） — Next.js ビルドと実行時オプション

## 開発サーバー設定

ワークスペースには `.claude/launch.json` に 2 つのサーバー設定が含まれています：
1. **`cursor-example (Next.js dev)`** — 開発モード（自動リロード、ポート 3000、autoPort 有効）
2. **`cursor-example (Next.js start)`** — 本番相当のサーバー（ポート 3000）

Claude Code から `/preview_start` を使用して開発サーバーを起動します。

## 大量のタスク処理

大規模または複雑な多面的なタスクが発生した場合は、**Team Agent**（`/team-agent` または複数のサブエージェントを持つ Agent ツール）を使用して、独立したストリーム間で作業を並列化してください。これにより、順序処理ではなく、並行した調査、実装、テストが可能になります。

例：
- 複数の独立した機能を実装する必要がある場合
- コードベース全体にわたる包括的なリファクタリング
- 複数の接点を持つ複雑なアーキテクチャの変更
- 大規模なテストまたはマイグレーション作業
