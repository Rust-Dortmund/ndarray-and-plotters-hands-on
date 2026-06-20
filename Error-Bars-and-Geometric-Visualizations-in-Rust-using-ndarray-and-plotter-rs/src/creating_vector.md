# Creating a vector


Define the the vector:

```
let min: f32 = 0.0;
let max: f32 = 10.0;
let stepwidth: f32 = 1.0;
let number: usize = 11;
```

## Creating a vector with a specefic numer of elements

```
let array_1: Array1<f32> = Array1::linspace(min, max, number);
println!("{:?}", array_1);
```


## Creating a vector with a given stepwidth

```
let array_2: Array1<f32> = (0..)
    .map(|v| min + v as f32 * stepwidth)
	.take_while(|&x| x <= max)
	.collect();
	
println!("{:?}", array_2);
```


