# Hello World from http

to create simple web apps to print "hello world" in the browser, you need to put this into `main.go` and run

```go
package main

import (
	"fmt"
	"log"
	"net/http"
)

func main() {

	http.HandleFunc("/hello", func(rw http.ResponseWriter, r *http.Request) {
		fmt.Fprintln(rw, "Hello World")
	})

	fmt.Printf("server run on localhost:8000\n")
	if err := http.ListenAndServe(":8000", nil); err != nil {
		log.Fatal(err)
	}
}
```