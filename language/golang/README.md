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

golang concurency: goroutine in press keyboard

```
package main

import (
	"fmt"

	"github.com/eiannone/keyboard"
)

var char rune

func main() {
	fmt.Println("Press any key, or q to quit")

	_ = keyboard.Open()
	defer func() {
		keyboard.Close()
	}()

	for {
		char, _, _ = keyboard.GetSingleKey()
		if char == 'q' || char == 'Q' {
			break
		}
		listenForKeyPress()
	}

}

func listenForKeyPress() {
	fmt.Println("you pressed", string(char))
}
```
