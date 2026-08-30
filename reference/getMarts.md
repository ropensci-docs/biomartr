# Retrieve information about available Ensembl Biomart databases

This funcion queries the Ensembl Biomart API and returns a table storing
information about all available Ensembl Biomart databases.

## Usage

``` r
getMarts(update = FALSE)
```

## Arguments

- update:

  logical, default FALSE. If FALSE, use cached file if it exists. Set to
  TRUE to force new update

## See also

Other biomaRt:
[`biomart()`](https://docs.ropensci.org/biomartr/reference/biomart.md),
[`getAttributes()`](https://docs.ropensci.org/biomartr/reference/getAttributes.md),
[`getDatasets()`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`organismBM()`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`organismFilters()`](https://docs.ropensci.org/biomartr/reference/organismFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# get a table of all available databases from Ensembl Biomart
getMarts()
 } # }
```
