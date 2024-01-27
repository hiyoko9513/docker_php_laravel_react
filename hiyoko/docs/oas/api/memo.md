gen
```shell
$ docker run --rm -v $(PWD):/spec redocly/cli:latest bundle root.yml -o root.gen.yml
```
ui
```shell
$ docker run -p 8081:8080 -v $(PWD)/$(WORK_DIR):/usr/share/nginx/html/api -e API_URL=api/root.gen.yml swaggerapi/swagger-ui
```
mock
```shell
$ docker run --rm -it -p 4010:4010 -v $(PWD):/tmp stoplight/prism:4 mock -h 0.0.0.0 /tmp/root.gen.yml
```
