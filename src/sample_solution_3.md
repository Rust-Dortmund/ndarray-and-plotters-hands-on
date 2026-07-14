# Sample solution Exercise 3

```rust
:dep ndarray = "0.17.2"
:dep num-traits = "0.2.19"
:dep plotters = { version = "^0.3.0", default-features = false, features = ["evcxr", "all_series"] }
:dep rand = "0.10.2"

use num_traits::pow;
use plotters::prelude::*;
use ndarray::Array1;
use rand;

let u_in: Array1<f32> = Array1::linspace(0.0, 5.0, 51);
let u_out: Array1<f32> = u_in.mapv(|v| 0.7 * v - 1.4 + rand::random::<f32>());

let points: Vec<(f32, f32)> = u_in.into_iter().zip(u_out).collect();

// calculate
let n: f32 = points.len() as f32;

let mut sum_x: f32 = 0.0;
for i in points.clone().iter() {
    sum_x = sum_x + i.0;
}

let mut sum_y: f32 = 0.0;
for i in points.clone().iter() {
    sum_y = sum_y + i.1;
}

let mut sum_xx: f32 = 0.0;
for i in points.clone().iter() {
    sum_xx = sum_xx + pow(i.0, 2 as usize);
}

let mut sum_xy: f32 = 0.0;
for i in points.clone().iter() {
    sum_xy = sum_xy + i.0 * i.1;
}

let a: f32 = (sum_xy - sum_x * sum_y / n) / (sum_xx - pow(sum_x, 2 as usize) / n);
let b: f32 = (sum_y - a * sum_x) / n;

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

    chart.draw_series(PointSeries::of_element(
        points.clone(),
        5,
        &RED,
        &|c, s, st| {
            return EmptyElement::at(c)    // We want to construct a composed element on-the-fly
            + Circle::new((0,0),s,st.filled()) // At this point, the new pixel coordinate is established
        },
    ))?;

    chart.draw_series(LineSeries::new(
        (-1..=6).map(|x| x as f32).map(|x| (x, a * x + b)),
        &GREEN,
    ))?;


    Ok(())
})
```
