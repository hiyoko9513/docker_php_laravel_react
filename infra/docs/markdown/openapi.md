# openapi
## laravel
ドキュメント  
https://openapi-generator.tech/docs/generators/php/  
https://openapi-generator.tech/docs/generators/php-laravel/
apiディレクトリのlaravelに生成  
laravelをまるまる生成するようなコードなため、必要なもののみコピーするようなshellファイルを作成して運用するのが良さそう。  
そもそも、ただのPHPで生成する方がいいかも。  
```shell
$ make docker/oapi/api/php/codegen
```

infra想定(WIP)
```shell
#!/bin/bash
source ./.env

WORK_PATH='/tmp'
OUTPUT_PATH='../project/app/OpenAPI'

# apiディレクトリのコード生成
docker run --rm -v $(PWD)/$(WORK_DIR):/spec openapitools/openapi-generator-cli generate -i /spec/docs/oas/api/root.gen.yml -g php-laravel -o /spec/$* -c /spec/docs/oas/api/php-gen-config.json
# 必要なもののみ
cp -r ${WORK_PATH}/lib/* /spec/api/lib

rm -rf ${WORK_PATH}
```

## react
laravelと同様  
https://openapi-generator.tech/docs/generators/typescript-axios  
```shell
$ make docker/oapi/api/typescript/codegen
```
