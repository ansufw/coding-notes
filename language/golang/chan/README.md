# Channel

We can view channel as internal FIFO (first in, first out)

## Channel Syntax

- Channel are associated with a data type, `T`
- The zero value of channel, `var ch chan T`, is nil
- The syntax to declare a channel of type `T` is `ch := make(chan T)`
- Given the channel denoted by the variable ch
  - Sending is done with `ch <- data`; the arrow points into the channel as the data travels into it
  - Receiving is done with `data := <- ch`; the arrow points away from the channel as the data travels out of it. 
  
## Channel in Action

write this code and run

```
package main

import "time"

func main() {
	print("main func start\n")
	ch := make(chan string)
	go greet(ch)

	print("main func ready\n")

	r := <-ch
  
	print("main receive channel from greting\n")
	print("main func complete, result: ", r, "\n")
}

func greet(ch chan string) {
	print("greeting func start\n")

	ch <- "helooo"

	print("greeting func complete\n")
}
```

is it too fast?, let's add some time sleep function.

```
func main() {
	print("main func start\n")
	ch := make(chan string)
	go greet(ch)

	time.Sleep(3 * time.Second)
	print("main func ready\n")

	r := <-ch

	time.Sleep(2 * time.Second)
	print("main receive channel from greting\n")

	time.Sleep(1 * time.Second)
	print("main func complete, result: ", r, "\n")
}

func greet(ch chan string) {
	print("greeting func start\n")

	ch <- "helooo"

	print("greeting func complete\n")
}

```

Now add a buffer to channel in channel declaration `ch := make(chan string, 1)`, run, and see the difference



## Another note

https://www.tumblr.com/ansuf/700530434117943296/channel-introduction
https://www.tumblr.com/ansuf/tagged/concurrency

