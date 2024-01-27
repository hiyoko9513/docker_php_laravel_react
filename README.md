# docker template laravel & react
## 目的
1. ローカルでサブドメインを利用して複数のサイトを同時に立ち上げ
2. laravel10を利用してapiを開発
3. redis環境
4. ローカル用のメールサーバー
5. フロントにreactを利用
6. oapiからmockを立ち上げる

※注意  
コード補完を残すためにvendorとnode_modulesもマウントしている

## quick start
実行する場合、reactとlaravelプロジェクトを作成するので完了まで時間を要する
```shell
$ cd infra && make quickstart
```
https://lvh.me にアクセス

## 作業ディレクトリ
初期から設定されているサイトは
- https://lvh.me 
  - → react server(appフォルダ)
- https://api.lvh.me/
  - → apiフォルダ
- https://html.lvh.me
  - → htmlフォルダ

## 立ち上げ方
※上から順番に実行することを前提

1. infraディレクトリへ
```shell
$ cd infra
$ cp .env.example .env
```

2. reactプロジェクトの作成(既存は、appフォルダ名でworkディレクトリに配置)
```shell
$ docker-compose run --rm node npx create-react-app app --template typescript

# next jsの場合
$ docker-compose run --rm node npx create-next-app app --template typescript
```

3. laravelプロジェクトの作成(既存は、apiフォルダ名でworkディレクトリに配置)
```shell
$ docker-compose run --rm php composer create-project laravel/laravel api --prefer-dist
```

4. docker起動
```shell
$ docker-compose up -d
```

5. node packageをインストール 
reduxの場合
```shell
$ docker-compose run --rm -w /usr/src/app node npm install @types/react-redux @types/redux-logger --save-dev
```

https://lvh.me にアクセス


## コマンド
### package.jsonのスクリプト実行
```shell
$ docker-compose run --rm node npm run <スクリプト名> /usr/src/app
```

### scssのコンパイル
package.json
```text
"scripts": {
  "css/scss": "node-sass <scssのルートファイル> -o <アウトプットフォルダ> --output-style expanded",
}
```
コンパイル実行
```shell
$ docker-compose run --rm -w /usr/src/app node npm run css/scss
```

### mockサーバーの立ち上げ
```shell
$ make docker/oapi/mock
```
http://0.0.0.0:4010/v1/pets

### oapi uiサーバーの立ち上げ
```shell
$ make docker/oapi/ui
```
http://localhost:8081/


## infraディレクトリ
### サイトの増やし方メモ
1. nginxディレクトリのsitesディレクトリに`*.conf`ファイルを追加し、
2. docker-compose.ymlのhttps-portalのDOMAINを追加する。

### xdebug情報
phpフォルダのphp.iniに記載



typescript-fetch https://openapi-generator.tech/docs/generators/typescript-fetch で生成します。Generate client code by typescript-fetch option.

docker run --rm -v "${PWD}:/local" \
-u `id -u`:`id -g` \
openapitools/openapi-generator-cli generate \
-i /local/api.json \
-g typescript-fetch \
-o /local/src/api
--additional-properties withInterfaces=true
