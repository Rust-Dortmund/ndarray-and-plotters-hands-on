# Accessing elements of a vector

We can easily access elements of a vector and perforn operations on ist with the [mapv](https://docs.rs/ndarray/latest/ndarray/struct.ArrayRef.html#method.mapv) method.


## Include dependencies for the example

Include [num_traits](https://shadow.github.io/docs/rust/num_traits/pow/index.html)

```
:dep num-traits = "0.2.19"
use num_traits::pow;
```


## Example

A few decates ago the following eqution was used to calculate the normal body weight:

Normal weight = body weight in cm - 100:

```
let normal_weight_old: Array1<f32> = size_cm.mapv(|v| v - 100.0);

println!("{}", normal_weight_old);
```

In these days the BMI (= Body Mass Index) is used. The weight in kg is devided by the square of the size in m. A BMI value of 25 represents the upper limit of the normal weight.

The formula \\(BMI = \frac{weight}{size^2 }\\) should be equal to 25:

```
let normal_weight_new: Array1<f32> = size_cm.mapv(|v| pow(v/100.0, 2) * 25.0);

println!("{}", normal_weight_new);
```
