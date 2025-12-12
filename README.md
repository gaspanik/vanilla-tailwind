**Archived and moved**: [vite-vanilla-tailwind](https://github.com/gaspanik/vite-vanilla-tailwind) に移動しました。

# vanilla-tailwind

このプロジェクトは、Vite、Tailwind CSS、Lucideアイコンを使用したシンプルなフロントエンド環境です。

## ✨ 技術スタック

-   **リンター/フォーマッター**: [Biome](https://biomejs.dev/)
-   **ビルドツール**: [Vite](https://vitejs.dev/)
-   **CSSフレームワーク**: [Tailwind CSS](https://tailwindcss.com/)
-   **アイコン**: [Lucide](https://lucide.dev/)

## 🚀 利用可能なスクリプト

プロジェクトのルートディレクトリで以下のコマンドを実行できます。

-   `pnpm dev`: 開発サーバーを起動します。
-   `pnpm build`: プロダクション用にプロジェクトをビルドします。
-   `pnpm preview`: ビルドされたプロジェクトをプレビューします。
-   `pnpm lint`: Biomeを使ってコードのリントチェックを実行しまし、自動修正します。
-   `pnpm format`: Biomeを使ってコードのフォーマットを実行しまし、自動修正します。
-   `pnpm check`: Biomeを使ってコードのフォーマットとリントチェックを実行し、自動修正します。

## 💡 アイコンの使用方法

このプロジェクトでは [Lucide](https://lucide.dev/) を使用してアイコンを表示します。

1.  **HTMLにプレースホルダーを追加**
    アイコンを表示したい場所に `data-lucide` 属性を持つ要素を配置します。アイコン名は `data-lucide` の値として指定します。

    ````html
    // filepath: index.html
    // ...existing code...
    <body>
      <div class="flex min-h-screen flex-col items-center justify-center bg-gray-100">
        <div class="mt-4 flex items-center gap-2">
          <i data-lucide="home"></i>
          <h1 class="text-2xl font-bold">Hello world!</h1>
        </div>
      </div>
      <script type="module" src="/src/main.js"></script>
    </body>
    // ...existing code...
    ````

2.  **JavaScriptでアイコンを初期化**
    [`src/main.js`](src/main.js) で `lucide` から `createIcons` と使用したいアイコンをインポートし、`createIcons` 関数を実行して、対応する `data-lucide` 属性を持つ要素をSVGアイコンに置き換えます。

    https://lucide.dev/guide/packages/lucide#with-esmodules

    ````javascript
    // filepath: src/main.js
    import './style.css'
    import { createIcons, Home } from 'lucide';

    createIcons({
      icons: {
        Home
      }
    })
    ````
