# Basic Syntax

There are four important elements (or management command) in Docker: 
1. image
2. container
3. volume
4. network

## Common syntax

- list of the element run `docker <element> ls`, e.g. `docker volume ls`
- see help for using list command run `docker <element> ls --help`, e.g. `docker container ls --help`
- clean up the element run `docker <element> prune`, e.g. `docker image prune`
- see option flag for using prune `docker <element> prune --help`, e.g. `docker network prune --help`
- remove the element `docker <element> rm <option if any> <element_name or id> `
- see option for removing the element `docker <element> rm --help`
- see option for list of the elements and others management commands and the command list `docker --help`
- check command available in a management command, for instance `docker swarm --help`

## Tricks

### stop all container

 `docker kill $(docker ps -q)`

### remove all container

`docker rm $(docker ps -a -q)`

### filtering column

`docker ps | awk '{print $3}'`

### show volume related to container

`docker ps -a --no-trunc --format "{{.ID}}\t{{.Names}}\t{{.Mounts}}"`

source: 
- https://www.designcise.com/web/tutorial/whats-the-difference-between-docker-stop-and-docker-kill-commands
- https://typeofnan.dev/how-to-stop-all-docker-containers/
- https://docs.docker.com/engine/reference/commandline/ps/#formatting
- https://forums.docker.com/t/var-lib-docker-does-not-exist-on-host/18314/2
- https://www.reddit.com/r/docker/comments/bp9vy6/how_to_access_docker_volumes_from_host/


# Recipe

## Recipe 1: Building Simple Apps

create new go project `go mod init <name_project>` and paste this code into `main.go`

```go
package main

import (
	"github.com/gofiber/fiber/v2"
)

func main() {

	app := fiber.New()

	app.Get("/", func(c *fiber.Ctx) error {
		return c.SendString(":) Hello, World!")
	})

	app.Listen(":3000")
}
```



create `Dockerfile` and paste this code

```sh
FROM golang:1.17.4

WORKDIR /app


COPY go.mod /app/
COPY go.sum /app/

RUN go mod download

COPY . .

EXPOSE 3000

CMD ["go", "run", "main.go"]

```

To create image from this Dockerfile, run `docker build -t simpleapp .`. Then we can create container from this image by running `docker run --name simpleapp_container -d -p 8080:3000 simpleapp`.    

- `--name simpleapp_container` is the name of the cointainer
- `-d` daemon mode so the app will run quetely
- `-p 8080:3000` is port external:port internal
- `simpleapp` the name of container 


To create multiple container that connect each other, we can create `docker-compose.yml` and paste this code

```yaml
version: "3.3"
services:
 backend:
  build: .
  ports: 
   - "8080:8080"
  volumes:
   - .:/app
  depends_on:
   - db
 db:
  image: mysql:5.7.22
  restart: always
  environment:
   MYSQL_DATABASE: ambasador
   MYSQL_USER: root
   MYSQL_PASSWORD: root
   MYSQL_ROOT_PASSWORD: root
  volumes:
   - .dbdata:/var/lib/mysql
  ports:
   - 3306:3306
```
