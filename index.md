---
title: Connected Data Products Demo
---

This demo virtualizes a [NISAR](https://nisar.jpl.nasa.gov/) GUNW (Geocoded Unwrapped Interferogram) granule, a large HDF5 file of SAR data with chunked arrays, into an [Icechunk](https://icechunk.io/) store, then queries it without downloading or converting the original file.

Presented at the [Building Open Connected Scientific Data Products for the Cryosphere](https://englacial.com/hackdays) hackdays, April 2026.

## How it works

1. [VirtualiZarr](https://github.com/zarr-developers/VirtualiZarr) reads HDF5 metadata from NASA's S3 storage and creates virtual Zarr references (chunk byte offsets into the original file)
2. [Icechunk](https://icechunk.io/) persists those references in a versioned, git-like store
3. Anyone can open the Icechunk store with `xr.open_datatree` and reads fetch only the requested chunks on demand

No data is copied. The original HDF5 stays at NASA.

To explore how NISAR chunk manifests look interactively, see the [NISAR Manifest Explorer](https://github.com/virtual-zarr/nisar-manifest-explorer).

## Notebooks

1. [**Virtualize NISAR GUNW**](./01-virtualize-s3.ipynb): Create virtual references via S3 and persist to Icechunk
2. [**Virtualize NISAR GUNW (HTTPS)**](./01-virtualize-https.ipynb): Same via HTTPS (works from anywhere, Icechunk support in progress)
3. [**Query via Icechunk**](./02-query-icechunk.ipynb): Open the Icechunk store and query 10 random points
4. [**Query via h5netcdf**](./03-query-h5netcdf.ipynb): Query the same 10 points the traditional way (baseline)

## Prerequisites

- A [NASA Earthdata](https://urs.earthdata.nasa.gov/) account (free)
- Python 3.12+

## Running locally

```bash
git clone https://github.com/maxrjones/connected-data-products-demo
cd connected-data-products-demo
uv sync
uv run jupyter lab
```

## Serving the docs

```bash
uv run myst start
```
