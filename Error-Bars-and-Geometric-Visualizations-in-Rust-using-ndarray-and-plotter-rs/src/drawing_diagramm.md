# Drawing a Diagram

Useful link: [Plotters Tutorial with Jupyter](https://plotters-rs.github.io/plotters-doc-data/evcxr-jupyter-integration.html)


- Open a terminal, write `jupyter notebook`
    - opens a jupyter notebook in the browser
	- click the button *new* on the upper right
	- choose **rust**
- Include [num_traits](https://shadow.github.io/docs/rust/num_traits/pow/index.html) and [plotters-rs](https://github.com/plotters-rs/plotters)

```
:dep num-traits = "0.2.19"
:dep plotters = { version = "^0.3.0", default-features = false, features = ["evcxr", "all_series"] }

use num_traits::pow;
use plotters::prelude::*;
```

- Copy and paste teh following code snippet in a cell

```
evcxr_figure((640, 480), |root| {
    let root = root.titled("2D Plotting", ("Arial", 20).into_font())?;
    
    let mut chart = ChartBuilder::on(&root)
        .caption("Normal weight = f(size)", ("Arial", 20).into_font())
        .x_label_area_size(40)
        .y_label_area_size(40)
        .build_cartesian_2d(150f32..200f32, 50f32..100f32)?;
    
    chart.configure_mesh()
        .x_desc("Size / cm")
        .y_desc("Weight / kg")
        .draw()?;
    
    // Old weight: Bodysize in cm - 100
    chart.draw_series(LineSeries::new(
        (150..=200).map(|x| x as f32).map(|x| (x, x - 100.0)),
        &RED,
    ))?;
    // New weight: Body Mass Index = 25
    chart.draw_series(LineSeries::new(
      (150..=200).map(|x| x as f32).map(|x| (x, 25.0 * pow(x / 100.0, 2))),
      &GREEN,
    ))?;
    
    Ok(())
})
```
