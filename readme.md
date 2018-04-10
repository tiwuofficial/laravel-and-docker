# Init

```
git clone --recursive https://github.com/tiwuofficial/laravel-and-docker.git
cd laravel-and-docker
cp env-example .env
docker-compose up -d workspace
docker exec -it laradock_workspace_1 /bin/bash
composer install
cp .env.example .env
php artisan key:generate
exit
docker-compose up -d php-fpm nginx mysql
```

# Url

[http://localhost:8080/](http://localhost:8080/)