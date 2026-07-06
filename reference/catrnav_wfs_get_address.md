# WFS INSPIRE: download addresses

Retrieve spatial address data from the Cadastre of Navarre WFS INSPIRE
service. `catrnav_wfs_get_address_bbox()` retrieves objects included in
the provided bounding box. See **Bounding box**.

## Usage

``` r
catrnav_wfs_get_address_bbox(x, srs = 4326, verbose = FALSE, count = NULL)
```

## Arguments

- x:

  See **Bounding box**. Can be one of:

  - A numeric vector of length 4 with the coordinates that define the
    bounding box: `c(xmin, ymin, xmax, ymax)`.

  - A `sf/sfc` object, as provided by the
    [sf](https://CRAN.R-project.org/package=sf) package.

- srs:

  SRS/CRS to use in the query. Defaults to `4326`. See **Bounding box**.

- verbose:

  Logical. If `TRUE`, displays informational messages.

- count:

  Positive whole number specifying the maximum number of features to
  return. If `NULL`, the service default applies.

## Value

An [`sf`](https://r-spatial.github.io/sf/reference/sf.html) object.
Returns `NULL` if the data cannot be retrieved.

## API limits

The service returns a maximum of 5,000 features by default. Use `count`
to request a smaller result.

## Bounding box

When `x` is a numeric vector, make sure that `srs` matches the
coordinate values. The function queries the bounding box in
[EPSG:25830](https://epsg.io/25830), ETRS89 / UTM zone 30N, then
transforms the result back to `srs`.

When `x` is an [`sf`](https://r-spatial.github.io/sf/reference/sf.html)
or `sfc` object, `srs` is ignored. The object's bounding box is used for
the query and the result is transformed back to the input CRS. See
[`sf::st_bbox()`](https://r-spatial.github.io/sf/reference/st_bbox.html).

## References

[SITNA – Catastro de Navarra](https://geoportal.navarra.es/es/inspire)

## See also

Query data from WFS INSPIRE services:
[`catrnav_wfs_get_buildings_bbox()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_wfs_get_buildings.md),
[`catrnav_wfs_get_parcels_bbox()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_wfs_get_parcels.md)

Work with cadastral addresses:
[`catrnav_atom_get_address()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_address.md),
[`catrnav_atom_get_address_db_all()`](https://ropenspain.github.io/CatastRoNav/reference/catrnav_atom_get_address_db.md)

## Examples

``` r
downtown <- c(-1.646812, 42.814528, -1.638036, 42.820320)

ad <- catrnav_wfs_get_address_bbox(downtown, srs = 4326)

library(ggplot2)

ggplot(ad) +
  geom_sf()
```
