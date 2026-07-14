# Creating a vector

Let's calculate a line as we know from school: `f(x) = bx + a;` and store it in memory.

We want to explore several ways that lead to the same vector.

## Include dependencies

Include [ndarray](https://docs.rs/ndarray/latest/ndarray/)

```rust
:dep ndarray = "0.17.2"
use ndarray::Array1;
```


## Define the the vector:

```rust
let min: f32 = 150.0;
let max: f32 = 200.0;
let stepwidth: f32 = 1.0;
let number: usize = 51;
```


## Creating a vector with a specific number of elements

```rust
let size_cm: Array1<f32> = Array1::linspace(min, max, number);

println!("{:?}", size_cm);
```


## Creating a vector with a given stepwidth

```rust
let size_cm_2: Array1<f32> = (0..)
    .map(|v| min + v as f32 * stepwidth)
	.take_while(|&x| x <= max)
	.collect();
	
println!("{:?}", size_cm_2);
```

Are both vectors equal?

```rust
println!("Both vectors are equal: {}", size_cm == size_cm_2);
```
