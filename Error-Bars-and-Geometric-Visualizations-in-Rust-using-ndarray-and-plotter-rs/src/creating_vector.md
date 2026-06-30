# Creating a vector

## Include dependencies

Include [ndarray](https://docs.rs/ndarray/latest/ndarray/) and [num_traits](https://shadow.github.io/docs/rust/num_traits/pow/index.html)

```
:dep ndarray = "0.17.2"
:dep num-traits = "0.2.19"

use ndarray::Array1;
use num_traits::pow;
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


## Calculations

A few decates ago the following eqution was used to calculate the normal body weight:

Normal weight = body weight in cm - 100

```
let normal_weight_old = size_cm.mapv(|v| v - 100.0);

println!("{}", normal_weight_old);
```

In these days the BMI (= Body Mass Index) is used. The weight in kg is devided by the square of the size in m. A BMI value of 25 represents the upper limit of the normal weight.

The formula \\(BMI = \frac{weight}{size^2 }\\) should be equal to 25.

```
let normal_weight_new = size_cm.mapv(|v| pow(v/100.0, 2) * 25.0);

println!("{}", normal_weight_new);
```
