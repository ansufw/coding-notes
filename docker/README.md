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

	app.Listen(":8080")
}
```

create `Dockerfile` and paste this code

```bash
FROM golang:1.17.4

WORKDIR /app


COPY go.mod /app/
COPY go.sum /app/

RUN go mod download

COPY . .

CMD ["go", "run", "main.go"]
```

create `docker-compose.yml` and paste this code

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