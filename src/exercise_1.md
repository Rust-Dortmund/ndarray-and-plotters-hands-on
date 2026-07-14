# Exercise 1

## Create a vector

Create a vector *u_in* from 0 V to 5 V with more 51 elements.


## Apply a mathematical operation

Apply an operation to each elenent of this vector, use the function 0.7 * *u_in& - 1.4, and store it to *u_out_ideal*.


## Add noise

Add noise to the values. The crate [rand](https://docs.rs/rand/latest/rand/fn.random.html) could be used. Store the result to *u_out*.


## Plot data points to a Diagram


```
evcxr_figure((640, 480), |root| {
    let root = root.titled("2D Plotting", ("Arial", 20).into_font())?;

    let mut chart = ChartBuilder::on(&root)
        .caption("V_out = f(V_in)", ("Arial", 20).into_font())
        .x_label_area_size(40)
        .y_label_area_size(40)
        .build_cartesian_2d(0f32..11f32, 0f32..11f32)?;

    chart.configure_mesh()
        .x_desc("V_in / V")
        .y_desc("V_out / V")
        .draw()?;

// Please add Your solution of exercise 1!

    chart.draw_series(PointSeries::of_element(
        points,
        5,
        &RED,
        &|c, s, st| {
            return EmptyElement::at(c)    // We want to construct a composed element on-the-fly
            + Circle::new((0,0),s,st.filled()) // At this point, the new pixel coordinate is established
            + Text::new(format!("{:?}", c), (10, 0), ("sans-serif", 10).into_font());
        },
    ))?;

// Please add Your solution of exercise 2!

    Ok(())
})
```