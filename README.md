# docker template laravel & react
## 用途
1. ローカルでサブドメインを利用して複数のサイトを同時に立ち上げ
2. laravel10を利用してapiを開発
3. redis環境
4. ローカル用のメールサーバー
5. フロントにreactを利用
6. openapiからmockを立ち上げる
7. reactとlaravelのコードの自動生成

※注意  
- コード補完を残すためにvendorとnode_modulesもマウントしている
- reactが配置されない場合、起動しない
- docker内で複数composerコマンドを実行した場合、１日rate limitがかかる

## ドキュメント
- [クイックスタート](./infra/docs/markdown/quickstart.md)
- [サイトの立ち上げ手順](./infra/docs/markdown/quickstart.md)
- [コマンドリスト](./infra/docs/markdown/command-list.md)
- [サイトの増やし方](./infra/docs/markdown/add-site.md)
- [その他](./infra/docs/markdown/other.md)

## 作業ディレクトリ
初期から設定されているサイトは
- https://lvh.me 
  - → react server(appフォルダ)
- https://api.lvh.me/
  - → apiフォルダ
- https://html.lvh.me
  - → htmlフォルダ


## todo
- laravelのoapi-codegen
- reactのoapi-codegen
- laravel linter
- react linter
- laravel test
- react test
- oasにuserのパスだけは追加する
