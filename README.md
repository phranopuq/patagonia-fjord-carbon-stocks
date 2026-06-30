# Post-glacial carbon stocks of two restricted Patagonian fjord basins

R/Rmd code accompanying the manuscript:

Ríos et al. *Post-glacial carbon stocks from acoustic sediment volumes in
two restricted fjord basins, Patagonia (52°S)*. Geo-Marine Letters [DOI when assigned].

## Contents

- `CARBON_STOCKS.Rmd` — Main analysis notebook. Parameterised over basin via YAML
  `params: basin: "BC"` or `"BT"`. Performs: (i) sequential Gaussian simulation
  of seafloor and basal acoustic horizons; (ii) clipping to picked-thickness
  envelope; (iii) integration of carbon densities over the simulated thickness
  field; (iv) Monte Carlo propagation of geometric uncertainty over 1000
  realisations; (v) stratigraphic sensitivity comparison (Scenarios A and B).

## Inputs

Each script expects basin-specific CSV files in the working directory:
- `BC_surface.csv`, `BC_bottom.csv` — picked seafloor and basal horizons for BC.
- `BT_surface.csv`, `BT_bottom.csv` — same for BT.
- Each file has columns `x`, `y`, `z` (UTM zone 18S, EPSG:32718; z in metres
  below sea level).

Core geochemistry data are archived in PANGAEA: Ríos et al. (2020a, b),
DOIs https://doi.org/10.1594/PANGAEA.900787 (BT) and
https://doi.org/10.1594/PANGAEA.900786 (BC).

## Software requirements

R ≥ 4.5.2, with packages: `sf`, `sp`, `gstat`, `terra`, `ggplot2`, `dplyr`,
`patchwork`, `svglite`.

## How to reproduce

For each basin (BC, BT):
1. Open `CARBON_STOCKS.Rmd`.
2. In the YAML header, set `params: basin: "BC"` (or "BT").
3. Knit. This produces `CARBON_STOCKS_BC.html` (or `_BT.html`) and writes
   SVG/PNG figures to `figures_svg/`.

## Reproducibility

All simulations use a fixed random seed (`set.seed(123)` at the top of each
script). Re-running on a different machine should produce identical numerical
results.

## License

MIT License (see LICENSE file).
