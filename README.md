# Connected Data Products Demo

Virtualize [NISAR](https://nisar.jpl.nasa.gov/) GUNW data into an [Icechunk](https://icechunk.io/) store and query it without downloading or converting the original HDF5 file.

Presented at the [Building Open Connected Scientific Data Products for the Cryosphere](https://englacial.com/hackdays) hackdays, April 2026.

## Notebooks

| Notebook | Description |
|----------|-------------|
| `01-virtualize` | Create virtual Zarr references to NISAR GUNW and persist to Icechunk (S3) |
| `01-virtualize-https` | Same via HTTPS (works from anywhere, Icechunk support in progress) |
| `02-query-icechunk` | Query 10 random points from the Icechunk store |
| `03-query-h5netcdf` | Query the same 10 points via h5netcdf (baseline comparison) |

## Running locally

```bash
uv sync
uv run jupyter lab
```

Requires a [NASA Earthdata](https://urs.earthdata.nasa.gov/) account.
