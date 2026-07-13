# ATOM INSPIRE: download all buildings for a municipality

Retrieve spatial data for all buildings in a municipality using the ATOM
INSPIRE service provided by the Cadastre of Navarre.

## Usage

``` r
catrnav_atom_get_buildings(
  munic,
  cache = TRUE,
  update_cache = FALSE,
  cache_dir = NULL,
  verbose = FALSE
)
```

## Arguments

- munic:

  Municipality name, partial name or cadastral code. Use
  [`catrnav_atom_get_address_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_address_db.md)
  to inspect available municipalities.

- cache:

  Logical. Whether to use the cache. Defaults to `TRUE`.

- update_cache:

  Logical. Should the cached file be refreshed? Defaults to `FALSE`.
  When set to `TRUE`, it forces a new download.

- cache_dir:

  Path to a cache directory. On `NULL`, the function stores cached files
  in a temporary directory (see
  [`base::tempdir()`](https://rdrr.io/r/base/tempfile.html)).

- verbose:

  Logical. If `TRUE`, displays informational messages.

## Value

An [`sf`](https://r-spatial.github.io/sf/reference/sf.html) object.
Returns `NULL` if the data cannot be retrieved.

## References

[SITNA – Catastro de Navarra](https://geoportal.navarra.es/es/inspire)

## See also

Download data from ATOM INSPIRE services:
[`catrnav_atom_get_address()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_address.md),
[`catrnav_atom_get_address_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_address_db.md),
[`catrnav_atom_get_buildings_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_buildings_db.md),
[`catrnav_atom_get_parcels()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_parcels.md),
[`catrnav_atom_get_parcels_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_parcels_db.md),
[`catrnav_atom_search_munic()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_search_munic.md)

Work with cadastral buildings:
[`catrnav_atom_get_buildings_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_buildings_db.md),
[`catrnav_wfs_get_buildings_bbox()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_wfs_get_buildings.md)

## Examples

``` r

s <- catrnav_atom_get_buildings("Iruña")
#> ! Reading a large spatial file (25.2 Mb).

library(ggplot2)

ggplot(s) +
  geom_sf() +
  labs(
    title = "Buildings",
    subtitle = "Pamplona / Iruña"
  )
```
