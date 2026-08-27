# carp-matrix

A robust, low-level numerical matrix library for the [Carp language](https://github.com/carp-lang/Carp).

## Features

- **Safe & Unsafe API:** Choose between performance and safety with `Result`-returning functions or `unsafe-` variants.
- **True In-Place Mutation:** Memory-efficient operations like `add!`, `sub!`, and `hadamard!` that modify data without new allocations.
- **Cache-Aware Performance:** Optimized matrix multiplication using transposed layouts for better cache locality.
- **Zero-Copy Structural Ops:** Metadata-only `reshape` and `flatten` (currently behaves as copy due to Carp deftype semantics, but architected for minimal overhead).
- **Comprehensive API:** Includes `zeros`, `identity`, `random`, `transpose`, `dot`, `mat-vec`, `outer-product`, `approx=`, and more.
- **Rigorous Testing:** Deep verification of mathematical identities and edge cases.

## Installation

Add this to your project by loading `matrix.carp`.

```clojure
(load "path/to/carp-matrix/matrix.carp")
(use Mat)
```

## Running Tests

```bash
carp -x test/matrix_test.carp
```

## Examples

See [examples.md](examples.md) for usage examples.

## License

MIT
