# LAMP + Python3.7 Docker

---
# JIM
- Instala docker en [mac](https://docs.docker.com/desktop/install/mac-install/) o si está en otra plataforma revisa que tengas los comandos ``` $ docker version ``` y ``` $ docker-compose version ``` 
- Revisa el docker-compose.yml 
- Actualiza las claves del environment de mysql (lineas 23-24)
- En consola:
- ``` $ docker-compose up -d --build ```
- Una vez que baje todo y este corriendo
- ``` $ docker-compose ps ```
- para ver los puertos donde todo está funcionando
- Wordpress debe entrar solo poniendo localhost en el browser o con el puerto asignado de en el ``` $ docker-compose ps ```
- Para python utiliza la entrada de docker commands (linea 84).
---

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
# note: if there are 2 images w/ same name use the TAG
$ docker run -it image_name sh
$ docker run -it image_name:tag sh
# NGINX ❯ nginx.conf to increase the size of uploads
$ docker cp docker-wordpress_nginx_1:/etc/nginx/nginx.conf ./nginx/
# PHP ❯ get php.ini
$ docker cp docker-wordpress_php_1:/usr/local/etc/php/php.ini-production ./php/
```
