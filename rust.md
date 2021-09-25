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

### Hello world
{: .-prime}

#### hello.rs
{: .-file}

```rust
fn main() {
  println!("message");
}
```

```bash
$ cargo build
```

## Input

### Fake stdin
{: .-prime}

#### intput.rs
{: .-file}
```rust
use std::io::{Cursor,BufRead};
let mut f = Cursor::new("hello\nworld\n".to_string());
let mut s = String::new();
let _ = f.read_line(&mut s)?;
println!("input: {}", s);
```

```
hello world

```
