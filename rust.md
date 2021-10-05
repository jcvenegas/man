---
title: Rust
layout: 2017/sheet
prism_languages: [rust]
weight: -3
tags: [Featured]
category: Code
updated: 2020-06-21
---

## Getting started
{: .-three-column}

### Basics
{: .-prime}

#### main.rs
```rust
fn main() {}
```

### Data Structures
#### Struct
```rust
 struct S { x: T, y: T }
```
#### Enum
```rust
 enum E { A, B(), C {} }
```
#### Global variable
```rust
static X: T = T();
```
#### Const
```rust
const X: T = T();
```
#### Array
```rust
let array = [x1, x2, ..., xn]
let array = [x; Size]
let array = [T; Size]
```
#### Right-exclusive range
```rust
a..b
```
#### Right-exclusive range
```rust
a..=b
```
#### Full range
```rust
..
```

### References & Pointers
#### Shared reference
```rust
&S       // Shared reference
  &[S]   // Special slice
  &str	  // Special str slice ref
  &dyn T	// Special trait object 
```
### Types
#### Matrtix
```rust
let m = vec![vec![init_val;cols]; rows];
```
### Iterators
#### Iter
```rust
chain()
```
```rust
filter()
```
```rust
for_each()
```
```rust
map()
```
```rust
max()
```
```rust
max_by()
```
```rust
min()
```
```rust
reduce()
```
```rust
zip()
```
#### IntoIter
```rust
into_iter()
```


## Collections
### Queue
```rust
use std::collections::VecDeque;
```
#### New
```rust
let mut q = VecDeque::new();
```
#### Operations
```rust
q.push_back(Val);
```
```rust
q.pop_back(); // Option<T>: Some(Val)
```
#### Get by index
```rust
q.get(1);  // Option<T>: Some(&T))
````

### Map
```rust
use std::collections::HashMap;
```
#### New
```rust
let mut map = HashMap::new();
map.insert(key,val);
```
#### Operations
```rust
map.get(key); // Option<&V>
```
```rust
map.contains_key(key); // bool
```
```rust
map.remove(key);
```
#### Iter
```rust
for (k, v) in map.Iter() {}
```
```rust
for (_, val) in map.iter_mut() {
        *val= Val;
}
```

### Heap
```rust
use std::collections::BinaryHeap;
```
#### New
```rust
let mut heap = BinaryHeap::new();
```
#### New with custom comparator
```rust
use comparator::comparing;
let mut heap = 
  BinaryHeap::with_comparator(
    comparing(|s: &StructName| s.attr)
  );
```
#### Operations
```rust
heap.push(T);
```
```rust
heap.pop() // Option<T>
```
```rust
//get val but not pop
heap.peek() // Option<Val>
```
```rust
map.is_empty()
```
#### Reverse
```rust
use std::cmp::Reverse;
heap.push(Reverse(T));
heap.pop(); Option<Reverse(T)>
```

## Input
### Fake stdin
```rust
use std::io::{Cursor,BufRead};

// let mut stdin = io::stdin();
let mut stdin = Cursor::new("FAKE TEXT".to_string());

let mut s = String::new();
let _ = f.read_line(&mut s)?;
```
### Read from stdin
```rust
let mut buffer = String::new();
std::io::stdin().read_line(&mut buffer)?;
std::io::stdin().read_to_string(&mut buffer)?;
```


