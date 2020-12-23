# docker-wordpress
```
version: '3' -> docker compose version (required)

services: (required)
  wordpress:
    image: wordpress: 5.6-php7.4 -> image name
    environment: -> default variables on docker hub: https://hub.docker.com/_/wordpress
      WORDPRESS_DB_HOST: db -> "db", docker compose will auto networking services
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: 123456
      WORDPRESS_DB_NAME: wordpress
    volumes:
      - wordpress: /var/www/html
    ports: -> set a port
      - 8080: 80
    depends_on: -> "db" should be create first
      - db
    restart: always
  db:
    image: mysql:5.7 -> image name
    environment: -> default variables on docker hub: https://hub.docker.com/_/mysql
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: 123456
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - wordpress: /var/lib/mysql
    restart: always
volumes: -> data on container will be delete you delete container, so use "volumes" to save data (optional) 
	wordpress:
	db:
```

# command

- ``docker-compose up``
- ``docker-compose up -d`` -> detach mode, docker will run on background
- ``docker container ps``
- ``docker-compose ps``
- ``docker-compose stop``
- ``docker-compose config`` -> check yaml file
- ``docker-compose config -q`` -> check yaml file quiet mode
- ``docker-compose start`` -> restart container
- ``docker volume ls`` -> check dir
- ``docker inspect volume VOLUME_NAME`` -> check detail
- ``sudo ls -la VOLUME_DIR`` -> check dir folder
- ``docker-compose top`` -> check processing
- ``docker-compose top CONTAINER_NAME`` -> check processing detail
- ``docker-compose logs`` -> check logs
- ``docker container exec -it CONTAINER_ID /bin/bash`` -> access container
- ``docker-compose rm`` -> delete

# utils
- ``ipconfig``
