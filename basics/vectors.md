# Vectors

## 1. `Vec<T>::reserve()`

### Purpose

Ensures that a vector has enough additional capacity to accommodate a specified number of elements without reallocating.

### Signature

```rust
pub fn reserve(&mut self, additional: usize)
```

### Example

```rust
fn main() {
    let mut numbers: Vec<i32> = Vec::new();

    numbers.reserve(10);

    println!("Length: {}", numbers.len());       // 0
    println!("Capacity: {}", numbers.capacity()); // At least 10

    numbers.push(10);
    numbers.push(20);

    println!("{numbers:?}");
}
```

### Important Points

- Reserves additional capacity relative to the vector's current length, not its current capacity.
- Does not change the vector's length.
- Does not initialize additional elements.
- May trigger memory reallocation if the existing capacity is insufficient.
- Guarantees that the capacity will be at least `len() + additional` after the call.
- The actual capacity may be greater than requested.

### When to Use

Use `reserve()` when you know approximately how many elements you will add to a vector and want to reduce unnecessary memory reallocations.

---

## 2. `Vec<T>::shrink_to_fit()`

### Purpose

Attempts to reduce a vector's allocated capacity to match its current length.

### Signature

```rust
pub fn shrink_to_fit(&mut self)
```

### Example

```rust
fn main() {
    let mut numbers = Vec::with_capacity(100);

    numbers.extend([10, 20, 30]);

    println!("Length: {}", numbers.len());       // 3
    println!("Capacity: {}", numbers.capacity()); // At least 100

    numbers.shrink_to_fit();

    println!("Length: {}", numbers.len());       // 3
    println!("Capacity: {}", numbers.capacity()); // 3
}
```

### Important Points

- Attempts to reduce allocated memory.
- Does not change the vector's length or elements.
- May trigger memory reallocation.
- Does not guarantee that capacity will equal length.
- Useful when a vector has accumulated excess capacity that is no longer needed.

### When to Use

Use `shrink_to_fit()` when a vector has finished growing and you want to reduce its unused allocated capacity.

---

## 3. `Vec<u8>::extend_from_slice()`

### Purpose

Appends all elements from a slice to the end of a vector.

### Signature

```rust
pub fn extend_from_slice(&mut self, other: &[T])
where
    T: Clone
```

### Example

```rust
fn main() {
    let mut bytes: Vec<u8> = vec![1, 2, 3];

    let additional_bytes: &[u8] = &[4, 5, 6];

    bytes.extend_from_slice(additional_bytes);

    println!("{bytes:?}"); // [1, 2, 3, 4, 5, 6]
}
```

### Important Points

- Accepts a borrowed slice (`&[T]`).
- Appends a copy of each element to the vector.
- Does not consume or modify the original slice.
- Requires `T: Clone`.
- May trigger memory reallocation if the existing capacity is insufficient.
- In the case of `u8`, elements are copied because `u8` implements `Copy`.

### When to Use

Use `extend_from_slice()` when you want to append the contents of an existing slice to a vector without taking ownership of the source slice.

