# Config Ubuntu 20.04 and PHP

## 0. References

1. [configuration-php-dockerfile-from-ubuntu-image](https://stackoverflow.com/questions/60756815/configuration-php-dockerfile-from-ubuntu-image)
2. [php-fpm](https://php-fpm.org/)

## 1. Dockefile 
```
FROM ubuntu:20.04

RUN apt-get update

RUN apt-get install -y php-fpm
RUN apt-get install -y php-sqlite3 
RUN apt-get install -y sqlite3
```

## 2. Build Docker image
```
docker build -t php_sqlite:v1 .
```

## 3. Create docker container
```
docker run -it -v /workspace/gitpod_php/webapp:/webapp -p 8080 --name docker_php -h php php_sqlite:v1
```

## 4. Run PHP server

```
$cd /webapp
$php -S 0.0.0.0:8080
```

