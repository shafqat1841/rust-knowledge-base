# Strings

## 1. `String::chars()`

### Purpose

Returns an iterator over the Unicode scalar values (`char`) of a string.

### Signature

```rust
pub fn chars(&self) -> Chars<'_>
```

### Example

```rust
fn main() {
    let text = String::from("Rust");

    for character in text.chars() {
        println!("{character}");
    }
}
```

Output:

```text
R
u
s
t
```

### Important Points

- Returns an iterator of `char`.
- Does not consume or modify the original string.
- Iterates over Unicode scalar values, not individual UTF-8 bytes.
- Each `char` represents a Unicode scalar value and occupies 4 bytes in Rust.
- A Unicode scalar value can occupy between 1 and 4 bytes in UTF-8.
- It does not necessarily iterate over user-perceived characters (grapheme clusters).

### When to Use

Use `chars()` when you need to iterate over the characters of a string rather than its individual UTF-8 bytes.

---

## 2. `String::push_str()`

### Purpose

Appends a string slice (`&str`) to the end of an existing `String`.

### Signature

```rust
pub fn push_str(&mut self, string: &str)
```

### Example

```rust
fn main() {
    let mut text = String::from("Hello");

    text.push_str(" Rust");

    println!("{text}"); // Hello Rust
}
```

### Important Points

- Accepts a string slice (`&str`).
- Does not take ownership of the supplied string slice.
- Modifies the original `String`.
- Returns `()`.
- May allocate additional memory if the existing capacity is insufficient.
- The appended string is copied into the destination string.

### When to Use

Use `push_str()` when you want to append an existing string slice to a mutable `String` without taking ownership of the source.

---

## 3. `String::repeat()`

### Purpose

Creates a new `String` by repeating the contents of a string a specified number of times.

### Signature

```rust
pub fn repeat(&self, n: usize) -> String
```

### Example

```rust
fn main() {
    let text = "Rust";

    let repeated = text.repeat(3);

    println!("{repeated}"); // RustRustRust
}
```

### Important Points

- Takes the number of repetitions as a `usize`.
- Returns a new, owned `String`.
- Does not modify the original string.
- A repetition count of `0` produces an empty string.
- The resulting string requires memory allocation.
- Works with both `String` and `str` because the method is defined on `str`.

### When to Use

Use `repeat()` when you need to create a new string containing multiple consecutive copies of an existing string.

