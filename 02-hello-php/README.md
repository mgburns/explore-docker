
Let's try some more practical examples -- using Docker to bootstrap PHP environments for development.

Docker maintains several ["official"](https://docs.docker.com/docker-hub/official_repos/) repositories that contain base images for common development environments. Most of the commands in this file use images from the official PHP repository: https://hub.docker.com/_/php/


1. Run an interactive PHP console using PHP 5.5

	```
	docker run -it php:5.5-cli
	```

2. Execute a single PHP script using PHP 5.6

	```
	docker run --name php-test-app -v "$PWD:/usr/src/app" -w /usr/src/app php:5.6-cli php test.php
	```

3. DIY - Build a "dockerized" PHP application from scratch using the [base Debian image](https://hub.docker.com/_/debian/):

	```
	cd diy-phpapp

	# Build the image
	docker build -t mgburns/phpapp .

	# Run for production
	docker run --rm --name diy-phpapp mgburns/phpapp

	# Run for local development (mount current directory as a volume inside the container)
	docker run --rm -v "$PWD:/usr/src/app" --name diy-phpapp-dev mgburns/phpapp
	```

4. A more full featured PHP application using the latest version of PHP and Apache:

	```
	cd phpapp-apache

	# Build the image
	docker build -t mgburns/phpapp-apache .

	# Run for production
	docker run -d -p 80:80 --name phpapp-apache-prod mgburns/phpapp-apache

	# Run for local development
	docker run -d -v "$PWD/src:/var/www/html" -p 80:80 --name phpapp-apache-dev mgburns/phpapp-apache

	# Monitor the logs while developing
	docker logs -f phpapp-apache-dev
	```