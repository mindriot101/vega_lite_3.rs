# vega-lite v3 for rust

[![license](https://img.shields.io/crates/l/vega_lite_3.svg)](https://spdx.org/licenses/Apache-2.0.html)
[![version](https://img.shields.io/crates/v/vega_lite_3.svg)](https://crates.io/crates/vega_lite_3)
[![Release Doc](https://docs.rs/vega_lite_3/badge.svg)](https://docs.rs/vega_lite_3)

[![Actions Status](https://github.com/davidB/vega_lite_3.rs/workflows/ci-flow/badge.svg)](https://github.com/davidB/vega_lite_3.rs/actions)

A Rust api for vega-lite v3. Use it to generate vega-lite json, to display result in your Browser or in Jupyter (via [showata](https://crates.io/crates/showata)).

## Examples

[<img src="https://raw.githubusercontent.com/davidB/vega_lite_3.rs/master/examples/res/screens/scatterplot.png">](https://github.com/davidB/vega_lite_3.rs/blob/master/examples/scatterplot.rs)
[<img src="https://raw.githubusercontent.com/davidB/vega_lite_3.rs/master/examples/res/screens/stock_graph.png">](https://github.com/davidB/vega_lite_3.rs/blob/master/examples/stock_graph.rs)

```rust
    let values: Array2<f64> = Array::random((100, 2), StandardNormal);

    let chart = build!(VegaliteBuilder::default()
        .title("Random points")
        .data(values)
        .mark(Mark::Point)
        .encoding(build!(EncodingBuilder::default()
            .x(build!(XClassBuilder::default()
                .field("data.0")
                .def_type(StandardType::Quantitative)))
            .y(build!(YClassBuilder::default()
                .field("data.1")
                .def_type(StandardType::Quantitative))))));
    chart.show()?;
```

see [the full list of examples on github](https://github.com/davidB/vega_lite_3.rs/blob/master/examples/)

## Links

- [Wiki - AGuideToRustGraphicsLibraries2019](https://wiki.alopex.li/AGuideToRustGraphicsLibraries2019)
- [A Dramatic Tour through Python’s Data Visualization Landscape (including ggplot and Altair) – Regress to Impress](https://dsaber.com/2016/10/02/a-dramatic-tour-through-pythons-data-visualization-landscape-including-ggplot-and-altair/)
- [Specifying Data in Altair — Altair 3.0.0 documentation](https://altair-viz.github.io/user_guide/data.html#long-form-vs-wide-form-data)
- [Visualization — list of Rust libraries/crates // Lib.rs](https://lib.rs/visualization)
- [Quicktype](https://quicktype.io/) (got issue with the alternative https://transform.now.sh/json-to-rust-serde) was used to bootstrap `vegalite.rs` from the [vega-lite's json schema](https://vega.github.io/schema/vega-lite/v3.json)
