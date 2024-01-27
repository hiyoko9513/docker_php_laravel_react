# コマンド
## package.jsonのスクリプト実行
```shell
$ docker-compose run --rm node npm run <スクリプト名> /usr/src/app
```

## scssのコンパイル
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

## mockサーバーの立ち上げ
```shell
$ make docker/oapi/mock
```
http://0.0.0.0:4010/v1/pets

## oapi uiサーバーの立ち上げ
```shell
$ make docker/oapi/ui
```
http://localhost:8081/
