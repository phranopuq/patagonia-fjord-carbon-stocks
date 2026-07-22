# Post-glacial carbon stocks of two restricted Patagonian fjord basins

R/Rmd code accompanying the manuscript:

Ríos et al. *Post-glacial carbon stocks in two restricted Patagonian fjord basins (52°S) 
using acoustic profiles and sediment cores*. Geo-Marine Letters [DOI when assigned].

## Contents
- `CARBON_STOCKS_GITHub.Rmd` — Main analysis notebook. Parameterised over basin
  via the YAML field `params: basin: "BC"` or `"BT"`. Performs: (i) sequential
  Gaussian simulation of the seafloor and basal acoustic horizons; (ii)
  clipping to the picked-thickness envelope; (iii) integration of carbon
  densities over the simulated thickness field; (iv) Monte Carlo propagation
  of geometric uncertainty over 1000 realisations; (v) stratigraphic
  sensitivity comparison (Scenarios A and B).

## Inputs
The notebook expects the following basin-specific files in the working
directory (none are included in this repository — see "Data availability"
below):

- `BC_surface.csv`, `BC_bottom.csv` — picked seafloor and basal acoustic
  horizon for BC. `BT_surface.csv`, `BT_bottom.csv` — same for BT.
  Columns: `x`, `y`, `z` (UTM zone 18S, EPSG:32718; z in metres below sea
  level).
- `BC_core.csv`, `BT_core.csv` — depocentre composite-core geochemistry.
  Columns: `depth` (cm), `DBD` (g cm⁻³), `TC`, `TOC` (wt%).
- `BC_area.shp`, `BT_area.shp` (with sidecar `.shx`, `.dbf`, `.prj` files) —
  basin outline polygon, same CRS as above.
- `Gravities_BC_BT.csv` — shared file with the upper-10-cm replicate gravity
  cores for both basins. Columns: `cores` (core ID, prefixed `BC`/`BT`;
  used to select the current basin), `depth`, `DBD`, `TC`, `TOC`.

## Data availability
Raw acoustic picks, core geochemistry, and basin outlines are not
distributed in this repository. Sediment-core data are archived in PANGAEA:
Ríos et al. (2020a, b) — https://doi.org/10.1594/PANGAEA.900787 (BT) and
https://doi.org/10.1594/PANGAEA.900786 (BC). Reformat the archived core data
into the `{basin}_core.csv` layout above before running the notebook.
Acoustic sub-bottom data and the picked seafloor/basal-horizon datasets are
available from the corresponding author on request.

## Software requirements
R ≥ 4.5.2, with packages: `sf`, `sp`, `gstat`, `terra`, `ggplot2`, `scales`,
`patchwork`.

## How to reproduce
For each basin (BC, BT):
1. Open `CARBON_STOCKS_GITHub.Rmd`.
2. In the YAML header, set `params: basin: "BC"` (or `"BT"`).
3. Knit. This produces `CARBON_STOCKS_BC.html` (or `_BT.html`), with all
   figures embedded inline in the HTML output.

## Reproducibility
All simulations use a fixed random seed (`set.seed(123)`). Results should be
closely reproducible across machines with matching R/package versions;
`fit.variogram()`'s internal numerical optimisation can introduce small
floating-point differences across very different R, gstat, or BLAS versions.

## License
MIT License (see LICENSE file).
