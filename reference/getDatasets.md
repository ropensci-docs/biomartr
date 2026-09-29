# Retrieve All Available Datasets for a BioMart Database

This funcion queries the BioMart API and returns a table storing all
available datasets for a selected BioMart databases.

## Usage

``` r
getDatasets(mart, mute_citation = FALSE)
```

## Arguments

- mart:

  a character string specifying the database (mart) for which datasets
  shall be listed.

- mute_citation:

  logical value indicating whether citation message should be muted.

## See also

Other biomaRt:
[`biomart()`](https://docs.ropensci.org/biomartr/reference/biomart.md),
[`getAttributes()`](https://docs.ropensci.org/biomartr/reference/getAttributes.md),
[`getMarts()`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`organismBM()`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`organismFilters()`](https://docs.ropensci.org/biomartr/reference/organismFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# search for available datasets
# getMarts()
# choose database: "ENSEMBL_MART_ENSEMBL"
head(getDatasets("ENSEMBL_MART_ENSEMBL"), 10)
} # }
```
