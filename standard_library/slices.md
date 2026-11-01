# Slices

## 1. `&mut [u8]::copy_within()`

### Purpose

Copies a range of elements within the same mutable slice to another position within that slice.

### Signature

```rust
pub fn copy_within<R>(&mut self, src: R, dest: usize)
where
    R: RangeBounds<usize>
```

### Example

```rust
fn main() {
    let mut numbers = [1, 2, 3, 4, 5];

    numbers.copy_within(0..3, 2);

    println!("{numbers:?}"); // [1, 2, 1, 2, 3]
}
```

### Important Points

- Copies elements from one range to another within the same slice.
- The source is specified using a range.
- The destination specifies the starting index where the copied elements will be placed.
- Handles overlapping source and destination ranges safely.
- Does not change the length of the slice.
- Requires the element type to implement `Copy`.
- Panics if the source range or destination range is out of bounds.
- Elements outside the destination range remain unchanged.

### When to Use

Use `copy_within()` when you need to move or duplicate elements within the same slice, such as shifting bytes or modifying data in place.

### Additional Example: Shifting Elements

```rust
fn main() {
    let mut bytes = [10, 20, 30, 40, 50];

    // Shift elements one position to the right.
    bytes.copy_within(0..4, 1);

    println!("{bytes:?}"); // [10, 10, 20, 30, 40]
}
```

