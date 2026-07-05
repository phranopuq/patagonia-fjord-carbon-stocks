# output/

Place the locally rendered HTML reports here:

- `CARBON_STOCKS_BC.html`
- `CARBON_STOCKS_BT.html`

These are tracked in version control (unlike `data/`) so that results can be
inspected directly on GitHub without re-running R. Generate them by knitting
`CARBON_STOCKS_GITHub.Rmd` once with `params: basin: "BC"` and once with
`params: basin: "BT"` (the YAML `knit:` callback writes them here
automatically).
