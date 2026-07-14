# Sample solution

## Create a vector

```
:dep ndarray = "0.17.2"
use ndarray::Array1;

let u_in: Array1<f32> = Array1::linspace(0.0, 5.0, 51);
```


## Apply a mathematical operation

```
let u_out_ideal: Array1<f32> = u_in.mapv(|v| 0.7 * v - 1.4);

```

## Add noies

```
:dep rand = "0.10.2"
use rand;

let u_out: Array1<f32> = let u_out: Array1<f32> = u_out_ideal.mapv(|v| v - 0.5 + rand::random::<f32>());
```

## Plot data points to diagram

```
:dep ndarray = "0.17.2"
:dep num-traits = "0.2.19"
:dep plotters = { version = "^0.3.0", default-features = false, features = ["evcxr", "all_series"] }
:dep rand = "0.10.2"

use num_traits::pow;
use plotters::prelude::*;
use ndarray::Array1;
use rand;

evcxr_figure((640, 480), |root| {
    let root = root.titled("2D Plotting", ("Arial", 20).into_font())?;

    let mut chart = ChartBuilder::on(&root)
        .caption("V_out = f(V_in)", ("Arial", 20).into_font())
        .x_label_area_size(40)
        .y_label_area_size(40)
        .build_cartesian_2d(-1f32..6f32, -2f32..4f32)?;

    chart.configure_mesh()
        .x_desc("V_in / V")
        .y_desc("V_out / V")
        .draw()?;

    let u_in: Array1<f32> = Array1::linspace(0.0, 5.0, 51);
    let u_out: Array1<f32> = u_in.mapv(|v| 0.7 * v - 1.4 + rand::random::<f32>());
    
    let points: Vec<_> = u_in.into_iter().zip(u_out).collect();

    chart.draw_series(PointSeries::of_element(
        points,
        5,
        &RED,
        &|c, s, st| {
            return EmptyElement::at(c)    // We want to construct a composed element on-the-fly
            + Circle::new((0,0),s,st.filled()) // At this point, the new pixel coordinate is established
        },
    ))?;

// Please add Your solution of exercise 2!

    Ok(())
})

```
