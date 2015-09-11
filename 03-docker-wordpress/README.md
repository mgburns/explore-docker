Docker + WordPress Quick Start

# Start a container for [MySQL](https://hub.docker.com/_/mysql/)
docker run --name wpdb -e MYSQL_ROOT_PASSWORD=super-secret-password -d mysql

# Start a container for [WordPress](https://hub.docker.com/_/wordpress/)
docker run --name wp --link wpdb:mysql -p 80:80 -d wordpress

# Open using the Docker machine IP in your browser
open http://`docker-machine ip default`

# Stop WordPress
docker stop wp wpdb

# Start it again
docker start wpdb wp

You can also leverage Docker Compose:

In docker-compose.yml:

```yml
wp:
  image: wordpress
  links:
    - db:mysql
  ports:
    - 80:80

db:
  image: mariadb
  environment:
    MYSQL_ROOT_PASSWORD: example
```
