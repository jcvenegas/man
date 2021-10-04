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
```rust
let mut buf = VecDeque::new();
```
```rust
buf.push_back(Val);
assert_eq!(buf.pop_back(), Some(Val));
```
#### Get by index
```rust
assert_eq!(buf.get(1), Some(&4));
````

### Map
```rust
use std::collections::HashMap;
```
```rust
let mut map = HashMap::new();
map.insert(key,val);
```
```rust
map.get(key); // Option<&V>
```
```rust
map.contains_key(key); // bool
```
```rust
map.remove(key);
```
