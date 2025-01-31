## Contoh pointer

```go
package main

import "fmt"

type answer struct {
	env *person
}

func newAnswer() *answer {
	return &answer{}
}

type person struct {
	Nama   string
	Alamat string
	Umur   int
}

func main() {
	// Variable a: Pointer ke struct Person
	a := &person{
		Nama:   "Budi",
		Alamat: "Jakarta",
		Umur:   30,
	}

	// Variable b: Pointer ke struct Person yang sudah ada nilainya
	b := &person{
		Nama:   "Ani",
		Alamat: "Surabaya",
		Umur:   25,
	}

	// Menampilkan nilai awal variable a
	fmt.Println("Nilai awal a:", a)

	// Menampilkan nilai awal variable c
	c := newAnswer()
	fmt.Println("Nilai awal c.env:", c.env)

	// Mengganti alamat yang ditunjuk variable a ke alamat yang ditunjuk variable b
	a = b

	// Mengganti alamat yang ditunjuk variable c ke alamat yang ditunjuk variable b
	c.env = b

	// Menampilkan nilai variable a setelah diganti
	fmt.Println("Nilai a setelah diganti:", a)

	// Menampilkan nilai variable c setelah diganti
	fmt.Println("Nilai c setelah diganti:", c.env)
}
```
