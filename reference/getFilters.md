# Retrieve All Available Filters for a Specific Dataset

This funcion queries the BioMart API and returns a table storing all
available filters for a specific dataset.

## Usage

``` r
getFilters(mart, dataset, mute_citation = FALSE)
```

## Arguments

- mart:

  a character string specifying the database (mart) for which datasets
  shall be listed.

- dataset:

  a character string specifying the dataset for which filters shall be
  listed.

- mute_citation:

  logical value indicating whether citation message should be muted.

## See also

[`getMarts`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`getDatasets`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`getAttributes`](https://docs.ropensci.org/biomartr/reference/getAttributes.md),
[`organismBM`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`organismFilters`](https://docs.ropensci.org/biomartr/reference/organismFilters.md),
[`organismAttributes`](https://docs.ropensci.org/biomartr/reference/organismAttributes.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# search for available datasets
# getMarts()
# choose database (mart): "ENSEMBL_MART_ENSEMBL"
# head(getDatasets(mart = "ENSEMBL_MART_ENSEMBL"), 10)
# choose dataset: "hsapiens_gene_ensembl"
head(getFilters(mart = "ENSEMBL_MART_ENSEMBL",
                dataset = "hsapiens_gene_ensembl") , 5)
} # }
```
