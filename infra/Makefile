include .env

up-build:
	docker-compose up -d --build
up:
	docker-compose up -d
build:
	docker-compose build --no-cache --force-rm
stop:
	docker-compose stop
down:
	docker-compose down
restart:
	@make down
	@make up-build
# oapi
docker/oapi/gen:
	docker run --rm -v $(PWD)/$(WORK_DIR):/spec redocly/cli:latest bundle oapi/root.yml -o oapi/root.gen.yml

docker/oapi/mock: docker/oapi/gen
	docker run --rm -it -p 4010:4010 -v $(PWD)/$(WORK_DIR)/oapi:/tmp stoplight/prism:4 mock -h 0.0.0.0 /tmp/root.gen.yml

docker/oapi/ui: docker/oapi/gen
	docker run -p 8081:8080 -v $(PWD)/$(WORK_DIR)/oapi:/usr/share/nginx/html/api -e API_URL=api/root.gen.yml swaggerapi/swagger-ui

# quick start
quickstart:
	cp .env.example .env &&\
	docker-compose run --rm react npx create-react-app app --template typescript &&\
	docker-compose run --rm php composer create-project laravel/laravel api --prefer-dist &&\
	docker-compose up -d
# git
git/commit-template:
	cp ../.github/.gitmessage.txt.example ../.github/.gitmessage.txt &&\
    git config commit.template ../.github/.gitmessage.txt &&\
    git config --add commit.cleanup strip
