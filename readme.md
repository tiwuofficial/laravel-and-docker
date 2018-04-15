# Init

```
git clone --recursive https://github.com/tiwuofficial/laravel-and-docker.git
cd laravel-and-docker/laradock
cp env-example .env
docker-compose up -d workspace
docker exec -it laradock_workspace_1 /bin/bash
composer install
cp .env.example .env
php artisan key:generate
exit
vi .env
vi mysql/my.cnf
docker-compose up -d php-fpm nginx mysql
docker exec -it laradock_workspace_1 php artisan migrate
```

# Url

[http://localhost:8080/](http://localhost:8080/)

## laradock/.env

macのapacheとmysqlとportが被るので変更する
他、mysqlの設定

```
# before
NGINX_HOST_HTTP_PORT=80
MYSQL_DATABASE=default
MYSQL_USER=default
MYSQL_PASSWORD=secret
MYSQL_PORT=3306
# after
NGINX_HOST_HTTP_PORT=8080
MYSQL_DATABASE=hoge
MYSQL_USER=laravel
MYSQL_PASSWORD=laravel
MYSQL_PORT=3308
```

## laradock/mysql/my.cnf

.envのmysqlのportを変更したため

```
# before
[mysqld]
sql-mode="STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
character-set-server=utf8
# after
[mysqld]
sql-mode="STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
character-set-server=utf8
port=3308
[client]
default-character-set=utf8
```