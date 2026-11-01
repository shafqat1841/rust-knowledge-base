# Debugging Macros

## 1. `debug_assert_eq!()`

### Purpose

Checks whether two expressions are equal and panics if they are not equal, but only when debug assertions are enabled.

### Syntax

```rust
debug_assert_eq!(left, right);
```

An optional custom panic message can also be provided:

```rust
debug_assert_eq!(left, right, "Values should be equal");
```

### Example

```rust
fn main() {
    let expected = 10;
    let actual = 10;

    debug_assert_eq!(expected, actual);

    println!("Values are equal");
}
```

### Example: Assertion Failure

```rust
fn main() {
    let expected = 10;
    let actual = 20;

    debug_assert_eq!(expected, actual);
}
```

When debug assertions are enabled, the program panics because the two values are not equal.

### Important Points

- Checks whether two expressions produce equal values.
- Panics when the values are not equal and debug assertions are enabled.
- Uses the `PartialEq` trait for comparison.
- Also requires `Debug` implementations for displaying the values in the panic message.
- Evaluates its expressions only when debug assertions are enabled.
- Debug assertions are normally enabled in debug builds and disabled in release builds.
- Their behavior can be controlled through the `debug_assertions` configuration setting.
- Should not be used for essential runtime validation or business logic.

### When to Use

Use `debug_assert_eq!()` to verify assumptions and catch programming mistakes during development without necessarily introducing the same checks into optimized release builds.

### Related Macros

- `assert_eq!()` - Checks equality in both debug and release builds.
- `debug_assert_eq!()` - Checks equality when debug assertions are enabled.
- `assert!()` - Checks whether a boolean expression is true.
- `debug_assert!()` - Checks a boolean expression when debug assertions are enabled.

