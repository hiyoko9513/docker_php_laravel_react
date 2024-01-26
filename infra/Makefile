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
# quick start
quickstart:
	cp .env.example .env &&\
	docker-compose run --rm node npx create-react-app app --template typescript &&\
	docker-compose run --rm php composer create-project laravel/laravel api --prefer-dist &&\
	docker-compose up -d
# git
git/commit-template:
	cp ../.github/.gitmessage.txt.example ../.github/.gitmessage.txt &&\
    git config commit.template ../.github/.gitmessage.txt &&\
    git config --add commit.cleanup strip
