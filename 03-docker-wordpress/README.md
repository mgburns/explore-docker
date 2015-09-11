
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

If all goes well you should see the WordPress install screen.

**ProTip**: You can stop the WordPress containers by running `docker stop wp wpdb`, and start them again by running `docker start wpdb wp`.

## With Docker Compose

[Docker Compose](https://docs.docker.com/compose/) is a tool that orchestrates multi-container deployments.

1. Create a `docker-compose.yml` file:

	```yml
	wp:
	  image: wordpress
	  links:
	    - wpdb:mysql
	  ports:
	    - 80:80

	wpdb:
	  image: mysql
	  environment:
	    MYSQL_ROOT_PASSWORD: example
	```

2. Run `docker-compose up` to bring up both containers.
