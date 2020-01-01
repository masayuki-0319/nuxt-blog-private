## 新規作成
- Frontend
  - $ docker-compose build
  - $ docker-compose run --rm src create-nuxt-app .
  - package.json を以下の通り修正
    ```json:package.json
    ...
    "scripts": {
      "dev": "HOST=0.0.0.0 PORT=3000 nuxt",
    ...
    ```

## Contentful 設定
- $yarn add contentful @nuxtjs/dotenv @nuxtjs/markdownit node-sass sass-loader
- `nuxt.config.js`に設定追加

## Tips
- コンテナを停止
  - $ docker-compose stop
- コンテナを削除
  - $ docker-compose down
- コンテナ内に向けてコマンド送る
  - $ docker-compose run ~コンテナ名~ ~コマンド~
- コンテナ内で作業：単独
  - $ docker-compose run ~コンテナ名~ ash
- コンテナ内で作業：全体動作
  - $ docker-compose exec ~コンテナ名~ ash

## Referrence
- 環境構築
  - [Rails 6のDocker開発環境構築をEvil Martians流にやってみた](https://techracho.bpsinc.jp/hachi8833/2019_11_20/83450)
  - [dockerでnuxt\.jsの環境を作ってみる \- Qiita](https://qiita.com/reflet/items/e7c33f84ab43ab237ee4)
  - [【サーバーサイド一式】Docker \+ Rails \+ Circle CI \+ Terraformでインフラをコードで環境構築 & ECSへ自動コンテナデプロイ【前半】 \- Qiita](https://qiita.com/kazukimatsumoto/items/fa448e002b0afd441b7c#docker%E3%82%92%E7%94%A8%E3%81%84%E3%81%A6rails%E3%81%AE%E7%92%B0%E5%A2%83%E3%82%92%E6%A7%8B%E7%AF%89)
  - [marinaaisa/nuxt\-markdown\-blog\-starter: Nuxt \+ Markdown blog starter](https://github.com/marinaaisa/nuxt-markdown-blog-starter)
  - [docker\-compose＋MySQL5\.7\(8\.0も\)\+初期化\+永続化 \- Qiita](https://qiita.com/juhn/items/274e44ee80354a39d872)
- Nuxt ブログ構築
  - [Nuxt \+ Contentful \+ Netlifyでブログ作成全手順<前編> \- Izm Log](https://izm51.com/posts/nuxt-contentful-netlify-blog-making-1/)
  - [Content Delivery API \- access token](https://tech.itpropartners.jp/entry/2019/06/05/171553)
  - [【入門】Nuxt\.js \+ Contentful \+ Netlify で始める、JAMstack な CMS 構築 \- Qiita](https://qiita.com/isihigameKoudai/items/3e45ade7c438176a4cc9)
  - [ブログ構築カテゴリーの記事修正、更新情報 \- 独学プログラマ](https://blog.cloud-acct.com/posts/blog-entryupdate)
- Vuetify
  - [Vuetify\.js でお手軽マテリアルデザイン \+ Atomic Design「風」のディレクトリ構成 \- s平面の左側](https://blog.okashoi.net/entry/2017/12/19/103549)
  - [Vue\.js（Vuetify）とFirebaseで簡単なブログを公開して、ちょっとテストも書く \- Qiita](https://qiita.com/naoki85/items/1eb370c2bf64aaebf6d0)