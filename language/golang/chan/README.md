# Channel

We can view channel as internal FIFO (first in, first out)

## Channel Syntax

- Channel are associated with a data type, `T`
- The zero value of channel, `var ch chan T`, is nil
- The syntax to declare a channel of type `T` is `ch := make(chan T)`
- Given the channel denoted by the variable ch
  - Sending is done with `ch <- data`; the arrow points into the channel as the data travels into it
  - Receiving is done with `data := <- ch`; the arrow points away from the channel as the data travels out of it. 


## Sample

