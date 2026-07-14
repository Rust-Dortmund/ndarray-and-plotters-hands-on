# Introduction

This `mdbook` contains a Rust workshop featuring calculations and visualizations. It has been created by Günther Beulen of the Rust Dortmund Community. Find out more about our community at [MeetNTalk MVP - Rust Dortmund](https://meetntalk.rust-dortmund.de/events).

## Motivation

Let us calculate values and draw diagrams. If you're using Python for these tasks you'll find many similarities. But here, we'll stick to Rust and see how far we get!

## Used crates

- [ndarray](https://docs.rs/ndarray/latest/ndarray/)
- [plotters-rs](https://github.com/plotters-rs/plotters)
- [Evaluation Context for Rust](https://github.com/evcxr/evcxr)
- [mdBook](https://rust-lang.github.io/mdBook/) - YOU should install that, see the [repository readme](https://github.com/Rust-Dortmund/ndarray-and-plotters-hands-on/blob/development/README.md).

The first two crates are dependencies actively used for the examples. `ndarray` is similar to `numpy` and `plotter-rs` allows plotting but has no similarities with a Python package. The third crate `evcxr` is required for the Jupyter interface as a Rust Kernel and `mdbook` is used to build this workshop book.
