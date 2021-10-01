---
title: Go
layout: 2017/sheet
prism_languages: [go, bash]
weight: -3
tags: [Featured]
category: Code
updated: 2020-06-21
---

## Getting started
{: .-three-column}

### Hello world
{: .-prime}

#### hello.go
{: .-file}

```go
package main
import "fmt"

func main() {
  fmt.Println("hello")
}
```
Every package file has to start with `package`.



### Variables

#### Variable declaration

```go
var msg string
msg = "Hello"
```

#### Shortcut of above (Infers type)

```go
msg := "Hello"
```

### Constants

```go
const Phi = 1.618
```

## Basic types
{: .-three-column}

### Strings

```go
str := "Hello" //type: string
```

```go
str := `Multiline
string`
```

### Numbers

#### Typical types

```go
num := 3          // int
num := 3.         // float64
num := 3 + 4i     // complex128
num := byte('a')  // byte (alias for uint8)
```

### Pointers
```go
i, j := 42, 2701
```
```go
p := &i  // point to i
```
{: data-line="1"}
```go
fmt.Println(*p) // read i with p
```
{: data-line="1"}
```go
*p = 21 // set i with p
```
{: data-line="1"}
```go
*p = *p / 37 // divide i with p
```
{: data-line="1"}

### Type conversions

```go
i := 2
f := float64(i)
u := uint(i)
```
#### type assertion
```
var i interface{} = "hello"
s := i.(string)
```
{: data-line="2"}

See: [Type conversions](https://tour.golang.org/basics/13)

<div style="page-break-after: always"></div>

## Arrays (static)
{: .-three-column}

### Define

```go
// var numbers [5]int
numbers := [...]int{0, 0, 0, 0, 0}
```

## Slices (dynamic arrays)
{: .-three-column}

### Define
```go
slice := []int{2, 3, 4}
```

#### Insert: `a.Insert(x, at(i))`
```go
a = append(a[:i], append([]T{x}, a[i:]...)...)
```
#### Append slice: `a.AppendSlice(b)`
```go
a = append(a, b...)
```
#### Copy: `b = a.Copy()`
```go
b := make([]T, len(a))
copy(b, a)
```
####  Cut: `a.DeleteRange(i,j)`
```go
a = append(a[:i], a[j:]...)
```
####  Delete: `a.Delete(at(i))`
```go
a = append(a[:i], a[i+1:]...)
```
#### Insert slice: `a.InsertSlice(b, at(i))`
```go
a = append(a[:i], append(b, a[i:]...)...)
```
#### Push: `a.Push(x)`
```go
a = append(a, x)
```
#### Pop: `a.Pop()`
```go
x, a = a[len(a)-1], a[:len(a)-1]
```
#### Push front: `a.PushFront(x)`
```go
a = append([]T{x}, a...)
```
#### Pop Front/Shift: `a.PopFront()`
```go
x, a = a[0], a[1:]
```
#### Sub slice: `a[i..j]`
```go
// high: non inclusive
s = a[low:high]
```
```go
a[:high] // from beining until high
a[low:] // from low until end
```
#### Sort: `a.sort()`
```go
import  "sort"
sort.Strings(strs)
sort.Ints(ints)
```
#### Reverse: `s.sort().reverse()`
```go
sort.Sort(sort.Reverse(sort.IntSlice(s)))
```


## Concurrency
{: .-three-column}

### Goroutines

```go
// A "channel"
ch := make(chan string)

// Start concurrent routines
go func(){ ch <- "Foo" }()
go func(){ ch <- "Bar" }()

// Read 3 results
fmt.Println(<-ch, <-ch)
```

### Buffered channels

```go
ch := make(chan int, 2)
ch <- 1
ch <- 2
//This wil fail, size is 2
ch <- 3
// fatal error:
// all goroutines are asleep - deadlock!
```


### read from multiple channels

```go
select {
case msg1 := <-c1:
	fmt.Println("received", msg1)
case msg2 := <-c2:
	fmt.Println("received", msg2)
}
```

### Closing channels

#### Closes a channel

```go
ch <- 1
ch <- 2
ch <- 3
close(ch)
```
{: data-line="4"}

#### Iterates across a channel until its closed

```go
for i := range ch {
  ···
}
```
{: data-line="1"}

#### Closed if `ok == false`

```go
v, ok := <- ch
```

See: [Range and close](https://tour.golang.org/concurrency/4)

### WaitGroup

```go
//import "sync"
  var wg sync.WaitGroup
  
  for _, item := range itemList {
    // Increment WaitGroup Counter
    wg.Add(1)
    go func(){doSomehing...}()
  }
  // Wait for goroutines to finish
  wg.Wait()
```

A WaitGroup waits for a collection of goroutines to finish. The main goroutine calls Add to set the number of goroutines to wait for. The goroutine calls `wg.Done()` when it finishes.
See: [WaitGroup](https://golang.org/pkg/sync/#WaitGroup)


## Error Handling

### Defer error check

```go
func function() (err error) {
  defer func(){
    if err != nil {
      err = fmt.Errof("Add Context(%s)",err)
    }
  }()
  //...
}
```

## Structs
{: .-three-column}

### Defining

```go
type Vertex struct {
  X int
  Y int
}
```
{: data-line="1,2,3,4"}

```go
 v := Vertex{1, 2}
```

See: [Structs](https://tour.golang.org/moretypes/2)


### Pointers to structs

```go
v := &Vertex{1, 2}
v.X = 2
```

Doing `v.X` is the same as doing `(*v).X`, when `v` is a pointer.

## Methods

### Receivers
```go
func (v Vertex) Abs() float64 {
  return math.Sqrt(v.X * v.X + v.Y * v.Y)
}
```
{: data-line="1"}

```go
v := Vertex{1, 2}
v.Abs()
```

### Mutation

```go
func (v *Vertex) Scale(f float64) {
  v.X = v.X * f
  v.Y = v.Y * f
}
```
{: data-line="1"}

```go
v := Vertex{6, 12}
v.Scale(0.5)
// `v` is updated
```

By defining your receiver as a pointer (`*Vertex`), you can do mutations.

See: [Pointer receivers](https://tour.golang.org/methods/4)

## Interfaces

### A basic interface
```go
type Inteface interface {
  InterfaceMethod() float64
}
```
#### Struct
```go
type Struct struct {}
```
#### Methods
```go
func (s Struct) InterfaceMethod() float64 {
  return 1.0
}
```

## Flow control
{: .-three-column}

### Switch

```go
switch day {
  case "sunday":
    doSomething()
  default:
    work()
}
```

See: [Switch](https://github.com/golang/go/wiki/Switch)

### For loop

```go
for i := 0; i <= 10; i++ {
  fmt.Println("i=", count)
}
```

See: [For loops](https://tour.golang.org/flowcontrol/1)

### For-Range loop

```go
entry := []string{"a","b","c"}
for i, val := range entry {
  fmt.Printf("i=%d, val=%s\n", i, val)
}
```

See: [For-Range loops](https://gobyexample.com/range)

### While loop

```go
n := 0
x := 42
for n != x {
  n := guess()
}
```

See: [Go's "while"](https://tour.golang.org/flowcontrol/3)

## Functions
{: .-three-column}

### Lambdas

```go
myfunc := func() bool {
  return x > 10000
}
```
{: data-line="1"}

Functions are first class objects.

### Multiple return types

```go
a, b := getMessage()
```

```go
func getMessage() (a string, b string) {
  return "Hello", "World"
}
```
{: data-line="2"}

### Named return values

```go
func split(sum int) (x, y int) {
  x = sum * 4 / 9
  y = sum - x
  return
}
```
{: data-line="4"}

By defining the return value names in the signature, a `return` (no args) will return variables with those names.

See: [Named return values](https://tour.golang.org/basics/7)
