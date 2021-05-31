# Config Ubuntu 20.04 and PHP

URL Reference [configuration-php-dockerfile-from-ubuntu-image](https://stackoverflow.com/questions/60756815/configuration-php-dockerfile-from-ubuntu-image)

0. dockerfile

```
FROM ubuntu:20.04

RUN apt-get update
RUN apt-get -y install software-properties-common
RUN add-apt-repository ppa:ondrej/php


RUN apt-get -y update 
RUN apt-get install -y php7.0 
RUN apt-get install -y php7.0-fpm 
RUN apt-get install -y php7.0-mysql 
RUN apt-get install -y php7.0-json 
RUN apt-get install -y php7.0-curl 
RUN apt-get install -y php7.0-sqlite3 
RUN apt-get install -y php7.0-xml 
RUN apt-get install -y php7.0-bcmath 
RUN apt-get install -y php7.0-zip 
RUN apt-get install -y php7.0-mbstring 
RUN apt-get install -y php-xdebug 
RUN apt-get install -y php-ast

RUN apt-get install -y sqlite3
```

1. Build Docker image
```
docker build -t php_sqlite:v1 .
```

2. Create docker container
```
docker run -it -v /workspace/gitpod_php/webapp:/webapp -p 8080 --name docker_php -h php php_sqlite:v1
```

3. Run PHP server

```
$cd /webapp

php -S 0.0.0.0:8080
```

