# Creating a vector

## Include dependencies

Include [ndarray](https://docs.rs/ndarray/latest/ndarray/)

```
:dep ndarray = "0.17.2"
use ndarray::Array1;
```


## Define the the vector:

```
let min: f32 = 150.0;
let max: f32 = 200.0;
let stepwidth: f32 = 1.0;
let number: usize = 51;
```


## Creating a vector with a specific number of elements

```
let size_cm: Array1<f32> = Array1::linspace(min, max, number);

println!("{:?}", size_cm);
```


## Creating a vector with a given stepwidth

```
let size_cm_2: Array1<f32> = (0..)
    .map(|v| min + v as f32 * stepwidth)
	.take_while(|&x| x <= max)
	.collect();
	
println!("{:?}", size_cm_2);
```

Are both vectors equal?

```
println!("Both vectors are equal: {}", size_cm == size_cm_2);
```
