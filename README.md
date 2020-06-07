# Users Crud

### Technologies
 - Laravel 7
 - Mysql
 - Docker

### Repositories

Clone these repositories beside docker directory:
 - [API](https://github.com/felipemeddeiros/crud-users-app-api) - please clone the repository as ***users-api***
 - [Client](https://github.com/felipemeddeiros/crud-users-app-client) - please clone the repository as ***users-application***

### Instructions

Get in the docker directory and execute
```sh
$ docker-compose up -d
```

#### API

```sh
$ docker container exec -it php-fpm composer install -d /var/www/users-api \
    && docker container exec -it php-fpm cp ./users-api/.env.example ./users-api/.env \
    && docker container exec -it php-fpm php ./users-api/artisan key:generate \
    && docker container exec -it php-fpm php ./users-api/artisan config:cache \
    && docker container exec -it php-fpm composer dump-autoload -d /var/www/users-api \
    && docker container exec -it php-fpm php ./users-api/artisan migrate --seed \
    && docker container exec -it php-fpm php ./users-api/artisan passport:install \
    && docker container exec -it php-fpm php ./users-api/artisan optimize:clear
```

#### Client

```sh
$ docker container exec -it php-fpm composer install -d /var/www/users-application \
    && docker container exec -it php-fpm cp ./users-application/.env.example ./users-application/.env \
    && docker container exec -it php-fpm php ./users-application/artisan key:generate \
    && docker container exec -it php-fpm php ./users-application/artisan config:cache \
    && docker container exec -it php-fpm composer dump-autoload -d /var/www/users-application \
    && docker container exec -it php-fpm php ./users-application/artisan optimize:clear
```

### Mapping hosts

You have to include this on your hosts file.
```text
127.0.0.1	users-api.local
127.0.0.1	users-application.local
```

>***hosts directory:***
**Windows**: C:/Windows/System32/Drivers/etc/hosts;
**Linux**: /etc/hosts

### Links

Now the system is available on the following link: 
 - Web: http://users-application.local
 - API: http://users-api.local 

There is one user registered, you can use him.
Email: teste@email.com
Password: password
