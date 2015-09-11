
Finally, let's take a look at a more complex example -- a multi-container deployment of WordPress.

1. Start a container for [MySQL](https://hub.docker.com/_/mysql/)

	```
	docker run --name wpdb -e MYSQL_ROOT_PASSWORD=super-secret-password -d mysql
	```

2. Start a container for [WordPress](https://hub.docker.com/_/wordpress/)

	```
	docker run --name wp --link wpdb:mysql -p 80:80 -d wordpress
	```

3. Open using the Docker machine IP in your browser


	```
	open http://`docker-machine ip default`
	```

4. Stop WordPress

	```
	docker stop wp wpdb
	```

5. Start it again

	```
	docker start wpdb wp
	```

Alternatively, you can use [Docker Compose](https://docs.docker.com/compose/):

In `docker-compose.yml`:

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

And then run `docker-compose up`.