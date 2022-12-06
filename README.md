# generative-art-gallery
## About
- URL
  - https://generative-art-gallery-sand.vercel.app/

generative-artリポジトリの作品とソースコードをまとめる

とりあえず以下のコマンドでプロジェクトを作成したところ
npx create-next-app@latest --typescript .

## How to deploy to Vercel
- 参考資料
  - https://www.youtube.com/watch?v=hL6bDTNQhAc
- Vercelダッシュボード
  - https://vercel.com/dashboard  

## Skills
- TypeScript
- Next.js
- React
- Vercel

## Study
### Next.jsのレンダリング方式について（記事にまとめる！）
- 参考Qiita：https://qiita.com/mt_816/items/cdd13e058a6fb7abe0b3
- 公式(日本語):https://nextjs-ja-translation-docs.vercel.app/docs/basic-features/pages
- 公式(英語)：https://nextjs.org/docs/basic-features/pages#server-side-rendering
- 参考記事：https://y-hiroyuki.xyz/next-js/pre-rendering
- 投稿するブログ：https://www.engilaboo.com/wp-admin/post.php?post=2778&action=edit
- 概要
  - プリレンダリング
    - 事前にHTMLを生成すること
    - 通常のReactアプリケーション(SPA)の場合、ユーザーがWebページにアクセスし、Webページを表示する時にブラウザ側でHTMLを生成する（クライアントサーバーレンダリング）
    - プリレンダリングでは、ユーザーがアクセスする前に事前にHTMLを生成し、その用意されたHTMLをユーザーに提供する方式となっています。そのため、ブラウザの負荷を下げて表示を高速化することができます。
    - 事前にHTMLが生成されているため、検索エンジンのクローラーに全てのコンテンツを見せることができる
      - SPAのSEOにおけるデメリットをカバー
    - Next.jsでは、デフォルトで全てのページでプリレンダリングが有効化されている
    - Next.jsでは、2種類のプリレンダリング方式（SSR・SSG）がある。
      - HTMLを生成するタイミングに違いがる
  - SSR(Server Side Rendering)
    - ユーザーがアクセスした時にサーバー側でHTMLを生成
    - SPAではブラウザ側でHTMLを生成していましたが、SSRではサーバー側でHTMLを生成し、レンダリング済みのHTMLをブラウザ側に提供
    - ブラウザの大半の仕事をサーバー側に任せ、ブラウザの仕事は最後の描画だけ
    - SSRは、リクエストごとにHTMLを生成するため、常に最新の状態をユーザーに見せることができる
  - SSG
    - アプリビルド時にHTMLを生成する
    - リクエストごとにHTMLを生成せず、事前にビルドされたHTMLを再利用する形となるため、SSRよりもさらに高速な表示が可能
      - 基本的にはSSGを使用することが推薦
      - リアルタイムにWebサイトの表示を変える用途がなければSSGで良さそう
  - 今回は？
    - リアルタイムに更新する必要性は全くないので、公式が推奨しているSSGを使う