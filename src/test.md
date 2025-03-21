# 测试页面

## 测试代码块嵌入

Ref: [https://rust-lang.github.io/mdBook/format/mdbook.html](https://rust-lang.github.io/mdBook/format/mdbook.html)

### 示例代码

```rust
fn main() {
    println!("Hello, world!");
}
```

### 可编辑代码

```rust,editable
fn main() {
    println!("Hello, world!");
}
```

### 会失败的代码

```rust,should_panic
fn main() {
    panic!("This is a panic!");
}
```

```rust,compile_fail
fn main() {
    let x: i32 = "I am not a number!";
}
```
