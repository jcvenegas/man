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

### Basics
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
#### Scanf
```go
fmt.Scanf("%s", &name)
```
#### cli args
```go
os.Args[index]//slice of args
```

### Control Flow
#### Switch
```go
switch day {
  case "sunday":
    doSomething()
  default:
    work()
}
```
#### For loop
```go
for i := 0; i <= 10; i++ {}
```
#### For-Range loop
```go
for i, val := range Slice {}
```
#### While loop
```go
for true {}
```

### Types
#### Variables
```go
var msg string
msg = "Hello"
```
#### Shortcut of above (Infers type)
```go
msg := "Hello"
```

#### Constants
```go
const Phi = 1.618
```
#### Types
```go
str := "Hello"
```
```go
str := `Multiline
string`
```
```go
num := 3          // int
num := 3.         // float64
num := 3 + 4i     // complex128
num := byte('a')  // byte (uint8)
```
### Pointers
```go
p := &i  // point to i
```
```go
val := *p // p.getVal() 
```
```go
*p = 21 // p.setVal()
```
```go
*p = *p / 37 // p.setVal(p.getVal()/37)
```
### Type conversions
```go
i := 2
f := float64(i)
u := uint(i)
```
#### type assertion
```
var i interface{} = "hello"
s, ok := i.(string) // string, bool
```
{: data-line="2"}
#### Arrays (static)
```go
var numbers [5]int
```
```go
numbers := [...]int{0, 0, 0, 0, 0}
```
### String
```go
strings.Split("Str", "sep")
```
### Structs
{: .-three-column}

#### Struct
```go
type StructName struct {
  X  T
  X T
}
```
{: data-line="1,2,3,4"}

### Interfaces
#### Interface definition
```go
type Inteface interface {
  IfaceMethod() ReturnType
}
```
#### Implement Interface
```go
func (s Struct) IfaceMethod() ReturnType {
  return Type
}
```

### Functions
#### Lambdas
```go
myfunc := func() ReturnType {}
```
{: data-line="1"}
#### Multiple return types
```go
a, b := FunctionName()
```
```go
func FunctionName() (a string, b string) {
  return a, b
}
```
{: data-line="2"}
#### Named return values
```go
func split(sum int) (x, y int) {
  return
}
```
{: data-line="4"}

### Regex
```go
import "regexp"
```
```go
r, _ := regexp.Compile("regex")
```
```go
mList:= r.FindAllString("Txt",-1)
```
```go
mIdx := r.FindAllStringIndex("Txt",-1)
```
```go
sList := r.FindAllStringSubmatch("Txt",-1)
```
```go
sIdx := r.FindAllStringSubmatchIndex("Txt", -1)
```

<div style="page-break-after: always"></div>

## Collections
{: .-three-column}
### Slice
#### New `slice.new()`
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
#### Sub slice: `a[i..j]`
```go
// high: non inclusive
s = a[low:high]
```
```go
a[:high] // from beining until high
a[low:] // from low until end
```
#### Sort: `a.Sort()`
```go
import  "sort"
sort.Strings(strs)
sort.Ints(ints)
```
#### Reverse: `s.Sort().Reverse()`
```go
sort.Sort(sort.Reverse(sort.IntSlice(s)))
```
### Slice as Queue
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

### Heap
#### Interface implementation
```go
import "container/heap"

type T int
type Heap []T

func (h Heap) Len() int{
	return len(h)
}
func (h Heap) Less(i, j int) bool {
	return h[i] < h[j]
}
func (h Heap) Swap(i, j int) {
	h[i], h[j] = h[j], h[i]
}
func (h *Heap) Push(x interface{}) {
	*h = append(*h, x.(T))
}
func (h *Heap) Pop() interface{} {
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[0:n-1]
	return x
}
```
#### heap.New()
```go
h := &Heap{}
```
#### heap.Push()
```go
heap.Push(h, T(1)) // O(log n)
```
#### heap.Pop()
```
val := heap.Pop(h).(T)
```

### HashMap
#### New `map.New()`
```go
m := make(map[string]int)
```
Nil map
```go
var m map[KeyType]ValueType
```

#### Set: `map.Set(key, val)`
```go
m[Key] = Val
```
#### Get : `map.Get()`
```go
val, ok := m["route"]
```
####  Delete: `map.Delete(Key)`
```go
delete(m, Key)
```
#### Iter: `map.Iter()`
```go
for key, value := range map {}
```
#### Sort: `a.Sort()`
```go
import "sort"
for k := range m {
    keys = append(keys, k)
}
sort.Ints(keys)
for _, k := range keys {}
```
#### Reverse: `s.Sort().Reverse()`
```go
sort.Sort(sort.Reverse(sort.IntSlice(s)))
```


## Concurrency
{: .-three-column}

### Channels
#### New: `channel.New()`
```go
// A "channel"
ch := make(chan string)
```
{: data-line="2"}
#### Write: `channel.Write(val)`
```go
// Start concurrent routines
go func(){ ch <- "Foo" }()
go func(){ ch <- "Bar" }()
```
{: data-line="2,3"}
#### Read: `val=channel.Read()`
```go
fmt.Println(<-ch, <-ch)
```
{: data-line="2"}

#### Buffered channel: `channel.New(size)`
```go
ch := make(chan int, 2)
```
```go
ch <- 1
ch <- 2
//This wil fail, size is 2
```
```go
ch <- 3
// fatal error:
// all goroutines are asleep - deadlock!
```
Write more than size is a runtime error.
#### read from multiple channels
```go
select {
case msg1 := <-c1:
	fmt.Println("received", msg1)
case msg2 := <-c2:
	fmt.Println("received", msg2)
}
```
#### Closing channels: `channel.Close()`
```go
close(ch)
```
#### Iter until Close
```go
for i := range ch {
  ···
}
```
#### Check closed: `channel.IsClosed()`
```go
v, ok := <- ch
```

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

### RWMutex
#### Read Write Mutex
```go
var counter = struct{
    sync.RWMutex
    val Val
}{}
```
#### Read Lock
```go
counter.RLock()
n := counter.val
counter.RUnlock() 
```
#### Write Lock
```go
counter.Lock()
counter.val = NewVal
counter.Unlock()
```

