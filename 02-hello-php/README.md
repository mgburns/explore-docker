
Let's try some more practical examples -- 

1. Run an interactive PHP console using the official PHP 5.5 CLI image (https://hub.docker.com/_/php/)

	```
	docker run -it php:5.6-cli
	```

2. Execute a single PHP script using the official PHP 5.6 image (https://hub.docker.com/_/php/)

	```
	docker run --name php-test-app -v "$PWD:/usr/src/app" -w /usr/src/app php:5.5-cli php test.php
	```

3. DIY - Build a PHP-powered application using the Debian base image

	```
	cd diy-phpapp
	docker build -t mgburns/phpapp .
	docker images
	docker run --rm --name diy-phpapp mgburns/phpapp
	docker run --rm -v "$PWD:/usr/src/app" --name diy-phpapp-dev mgburns/phpapp
	```

4. A more full featured PHP application using Apache

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