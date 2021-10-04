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
#### Read from stdin
```rust
let mut buffer = String::new();
std::io::stdin().read_line(&mut buffer)?;
std::io::stdin().read_to_string(&mut buffer)?;
```
#### Fake stdin
```rust
use std::io::{Cursor,BufRead};

// let mut stdin = io::stdin();
let mut stdin = Cursor::new("FAKE TEXT".to_string());

let mut s = String::new();
let _ = f.read_line(&mut s)?;
```
### Types
#### Matrtix
```rust
let m = vec![vec![init_val;cols]; rows];
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

