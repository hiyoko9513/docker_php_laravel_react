# 立ち上げ方
※上から順番に実行することを前提

1. infraディレクトリへ
```shell
$ cd infra
$ cp .env.example .env
```

2. reactプロジェクトの作成(既存は、appフォルダ名でworkディレクトリに配置)
```shell
$ docker-compose run --rm app npx create-react-app app --template typescript

# next jsの場合
$ docker-compose run --rm app npx create-next-app app --template typescript
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
