# Examples

Here are some common ways to use `carp-matrix`.

## Basic Creation and Arithmetic

```clojure
(use Mat)

(defn main []
  (let [m1 (Mat.zeros 2 2)
        m2 (Mat.unsafe-from-array 2 2 [1.0 2.0 3.0 4.0])
        m3 (Mat.unsafe-from-array 2 2 [5.0 6.0 7.0 8.0])
        res (Mat.unsafe-add &m2 &m3)]
    (println* "Result: " (str &res))))
```

## Matrix Multiplication

```clojure
(let [a (Mat.unsafe-from-array 2 3 [1.0 2.0 3.0 4.0 5.0 6.0])
      b (Mat.unsafe-from-array 3 2 [7.0 8.0 9.0 10.0 11.0 12.0])
      c (Mat.unsafe-mul &a &b)]
  (println* "Product: " (str &c)))
```

## In-Place Operations

Use `!` functions to avoid allocations in hot loops.

```clojure
(let [m (Mat.random 100 100)]
  (do
    (ignore (Mat.scalar-mul! &m 2.0))
    (ignore (Mat.add! m &m)) ; Double it again in-place
    (println* "Sum: " (Mat.sum &m))))
```

## Safe API (Result Handling)

```clojure
(let [m (Mat.zeros 2 2)]
  (match (Mat.row &m 5) ; Index out of bounds
    (Result.Success r) (println* "Row: " (str &r))
    (Result.Error msg) (println* "Failed: " msg)))
```
