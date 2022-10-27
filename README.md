# Wordpress Docker

## Docker

- Using
- Nginx
- mysql
- php
- phpmyadim
- wordpress
- wp-cli

### URL

https://wordpress-docker.test/

### PHPMYADMIN

http://wordpress-docker.test:8000/

### MYSQL Connect

```base
$ docker exec -it docker-lamp_mysql_1 mysql -uroot -p
```

**docker-lamp_mysql_1** stands for the MYSQL container name

- [more info](https://rednafi.github.io/digressions/database/2020/03/15/mysql-install.html)

### DOCKER Commands

```bash
# When something on the *.dockerfile changes
$ docker-compose up -d --build
# When something pull down all changes
$ docker-compose down -d --build
# Get containers active on project
$ docker-compose ps
# Get all containers active and its id
$ docker ps
# Copy files from image to folder
$ docker cp imageID:/file ./folder
```

### WP-CLI - [URL](https://wp-cli.org/)

```bash
# Get users
$ docker-compose run --rm wp user list
# Get plugins
$ docker-compose run --rm wp plugin list
```

#### Other tools

mkcert [documentation](https://github.com/FiloSottile/mkcert)

```bash
# login to the folder
$ cd /nginx/certs
# create the certificate
$ mkcert wordpress-docker.test
```

**NOTE:** remember to update the `etc/hosts` to be able to log to the domain.

#### Docker commands

```bash
# list images
$ docker image ls --all
# explore image
$ docker run -it image_name sh
# NGINX ❯ nginx.conf to increase the size of uploads
$ docker cp docker-wordpress_nginx_1:/etc/nginx/nginx.conf ./nginx/
# PHP ❯ get php.ini
$ docker cp docker-wordpress_php_1:/usr/local/etc/php/php.ini-production ./php/
```
