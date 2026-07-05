# data/

This folder is intentionally empty in the repository. Place the following
basin-specific input files here before knitting `CARBON_STOCKS_GITHub.Rmd`
(all excluded from version control via `.gitignore`):

| File | Columns | Notes |
| --- | --- | --- |
| `BC_surface.csv`, `BT_surface.csv` | `x`, `y`, `z` | Picked basin-floor (seafloor) horizon. UTM 18S, EPSG:32718; z in m below sea level. |
| `BC_bottom.csv`, `BT_bottom.csv` | `x`, `y`, `z` | Picked basal acoustic horizon (base of post-glacial fill). Same CRS/units. |
| `BC_core.csv`, `BT_core.csv` | `depth`, `DBD`, `TC`, `OC` | Depocentre composite-core geochemistry. depth in cm, DBD in g cm⁻³, TC/OC in wt%. |
| `BC_area.shp`, `BT_area.shp` (+ `.shx`, `.dbf`, `.prj`) | — | Basin outline polygon, same CRS as above. |
| `Gravities_BC_BT.csv` | `cores`, `depth`, `DBD`, `TC`, `OC` | Shared file, upper-10-cm replicate gravity cores for both basins. `cores` values are prefixed `BC`/`BT` and used by the notebook to select the current basin. |

## Where to get these files
- Sediment-core data (basis for `{basin}_core.csv` and `Gravities_BC_BT.csv`)
  are archived in PANGAEA: Ríos et al. (2020a, b) —
  https://doi.org/10.1594/PANGAEA.900787 (BT) and
  https://doi.org/10.1594/PANGAEA.900786 (BC). They will need light
  reformatting into the column layout above.
- Acoustic sub-bottom data and the picked seafloor/basal-horizon point sets
  (basis for `{basin}_surface.csv`, `{basin}_bottom.csv`, `{basin}_area.shp`)
  are available from the corresponding author on request.
