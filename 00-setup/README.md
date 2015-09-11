# Docker Setup

Using Docker on Max OS X is a bit tricky due to the fact that the underlying technologies that Docker utilizes (Linux containers) are not available natively.

Fortunately the tooling around Docker is maturing, and Mac OS X users have a nice suite of tools called the "Docker Toolbox" to make running Docker less of a pain.

The "Docker Toolbox" installs VirtualBox and creates a very lightweight Linux VM to run the Docker daemon.

## Install Steps

1. Install the [Docker Toolbox](https://www.docker.com/toolbox). This installs everything you need to start using Docker. (We'll assume you're using Mac OS X).
2. Open the `Docker Quickstart Terminal` application. This will launch a shell and start the `default` Docker VM.

	                        ##         .
	                  ## ## ##        ==
	               ## ## ## ## ##    ===
	           /"""""""""""""""""\___/ ===
	      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
	           \______ o           __/
	             \    \         __/
	              \____\_______/


	docker is configured to use the default machine with IP 192.168.99.100
	For help getting started, check out the docs at https://docs.docker.com

	bash-3.2$

3. Run `docker run hello-world` to verify your installation. You should see something like:

	Hello from Docker.
	This message shows that your installation appears to be working correctly.

	To generate this message, Docker took the following steps:
	 1. The Docker client contacted the Docker daemon.
	 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
	 3. The Docker daemon created a new container from that image which runs the
	    executable that produces the output you are currently reading.
	 4. The Docker daemon streamed that output to the Docker client, which sent it
	    to your terminal.

	To try something more ambitious, you can run an Ubuntu container with:
	 $ docker run -it ubuntu bash

	Share images, automate workflows, and more with a free Docker Hub account:
	 https://hub.docker.com

	For more examples and ideas, visit:
	 https://docs.docker.com/userguide/

For more information, visit the [Mac OS X installation instructions](https://docs.docker.com/installation/mac/).
