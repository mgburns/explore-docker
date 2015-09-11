
Let's take a closer look at what happend when you ran the `docker run hello-world` command:

1. It looked for an image called "hello-world". It will check locally first, and __pull__ it from the [Docker Hub](https://hub.docker.com) if it can't be found.
2. It __built__ a new container from the image.
3. It __ran__ the default command (`hello`)

**Pro Tip:** You can run `docker images` to see all images you have stored locally, `docker ps` to see any currently running containers, and `docker ps -a` to see all containers.

## Images and Dockerfiles

What does the `hello-world` image look like? Let's take a look at the [Dockerfile](https://github.com/docker-library/hello-world/tree/22ecfe456f254d5babe6e413bed2de77cfaba047)!

	FROM scratch
	COPY hello /
	CMD ["/hello"]

The `FROM` directive informs Docker that this image is built on top of the `scratch` image. (A special "base image").
The `COPY` directive asks Docker to copy the local `hello` executable into the container at the `/` (root) path.
The `CMD` directive asks Docker to execute the newly available `/hello` command, which simply prints out a few lines of text to the terminal and exits.

**Next**: [Hello, PHP!](../02-hello-php)
