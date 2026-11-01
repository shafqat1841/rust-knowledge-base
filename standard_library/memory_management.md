# Memory Management

## 1. `std::mem::take()`

### Purpose

Replaces a value with its default value and returns the original value.

### Signature

```rust
pub fn take<T>(dest: &mut T) -> T
where
    T: Default
```

### Example

```rust
use std::mem;

fn main() {
    let mut numbers = vec![1, 2, 3];

    let old_numbers = mem::take(&mut numbers);

    println!("Old numbers: {old_numbers:?}"); // [1, 2, 3]
    println!("New numbers: {numbers:?}");     // []
}
```

### Important Points

- Accepts a mutable reference to a value.
- Requires the type to implement the `Default` trait.
- Replaces the original value with `T::default()`.
- Returns the original value, transferring its ownership to the caller.
- Does not clone the original value.
- Particularly useful when moving a value out of a mutable reference.
- For a `Vec<T>`, the default value is an empty vector.

### When to Use

Use `mem::take()` when you need to move a value out of a mutable reference while leaving a valid default value in its original place.

### Related Concept

Compare `mem::take()` with `mem::replace()`:

- `mem::take()` replaces a value with its default value.
- `mem::replace()` replaces a value with a value you explicitly provide.

