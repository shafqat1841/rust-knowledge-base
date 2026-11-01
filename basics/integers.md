# Integers and Numeric Conversions

## 1. `usize::from()`

### Purpose

Converts a value into `usize` using the `From` trait.

### Signature

```rust
pub fn from<T>(value: T) -> usize
where
    usize: From<T>
```

### Example

```rust
fn main() {
    let value: u8 = 10;

    let converted_value = usize::from(value);

    println!("{converted_value}"); // 10

    let boolean = true;

    let number = usize::from(boolean);

    println!("{number}"); // 1
}
```

### Important Points

- Uses the `From` trait for conversion.
- Only works when the destination type implements `From` for the source type.
- Does not perform arbitrary numeric conversions.
- Unlike `as`, `From` represents conversions that are guaranteed to be valid.
- The availability of conversions depends on the source and destination types.

### When to Use

Use `usize::from()` when converting a supported type into `usize` safely, particularly when working with indexing, collection lengths, and capacities.

---

## 2. `u8::is_ascii_digit()`

### Purpose

Checks whether a `u8` value represents an ASCII decimal digit (`0-9`).

### Signature

```rust
pub const fn is_ascii_digit(&self) -> bool
```

### Example

```rust
fn main() {
    let digit = b'5';
    let letter = b'A';

    println!("{}", digit.is_ascii_digit()); // true
    println!("{}", letter.is_ascii_digit()); // false

    let number = 5;

    println!("{}", number.is_ascii_digit()); // false
}
```

### Important Points

- Checks only ASCII decimal digits (`0x30` through `0x39`).
- Returns `true` for bytes representing characters `0` through `9`.
- Returns `false` for letters, whitespace, symbols, and other byte values.
- It is particularly useful when processing UTF-8 strings as bytes.
- Unlike `char::is_digit()`, it does not accept a radix.

### When to Use

Use `is_ascii_digit()` when validating or processing ASCII numeric input, especially when working with byte slices or implementing parsers.

