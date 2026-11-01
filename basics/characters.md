# Characters

## 1. `char::is_digit()`

### Purpose

Checks whether a character represents a digit in a specified radix (base).

### Signature

```rust
pub fn is_digit(self, radix: u32) -> bool
```

### Example

```rust
fn main() {
    let character = 'F';

    println!("{}", character.is_digit(16)); // true
    println!("{}", character.is_digit(10)); // false

    let number = '9';

    println!("{}", number.is_digit(10)); // true
}
```

### Important Points

- Accepts a radix between `2` and `36`.
- Returns `true` if the character represents a valid digit in the specified radix.
- Supports numeric digits and alphabetic digits (`a-z` and `A-Z`) where applicable.
- For radix 16, characters `0-9`, `a-f`, and `A-F` are valid.
- It is not an ASCII-only digit check.
- Use `is_ascii_digit()` when you specifically need to check ASCII digits (`0-9`).

### When to Use

Use `is_digit()` when validating individual characters against a particular number system, such as binary, decimal, or hexadecimal.

---

## 2. `char::to_digit()`

### Purpose

Converts a character into its numeric digit value according to a specified radix.

### Signature

```rust
pub fn to_digit(self, radix: u32) -> Option<u32>
```

### Example

```rust
fn main() {
    let character = 'F';

    let digit = character.to_digit(16);

    println!("{digit:?}"); // Some(15)

    let invalid_character = 'G';

    let digit = invalid_character.to_digit(16);

    println!("{digit:?}"); // None
}
```

### Important Points

- Accepts a radix between `2` and `36`.
- Returns `Some(u32)` if the character can be converted.
- Returns `None` if the character is not a valid digit for the specified radix.
- The returned value represents the actual numeric value of the digit, not its character code.
- Alphabetic characters represent values from `10` onwards.
- The method is useful when parsing numbers represented as characters.

### When to Use

Use `to_digit()` when you need to convert a character into its numeric value, especially when implementing number parsing or converting between number systems.

