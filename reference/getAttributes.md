# Retrieve All Available Attributes for a Specific Dataset

This function queries the BioMart Interface and returns a table storing
all available attributes for a specific dataset.

## Usage

``` r
getAttributes(mart, dataset, mute_citation = FALSE)
```

## Arguments

- mart:

  a character string specifying the database (mart) for which datasets
  shall be listed.

- dataset:

  a character string specifying the dataset for which attributes shall
  be listed.

- mute_citation:

  logical value indicating whether citation message should be muted.

## See also

Other biomaRt:
[`biomart()`](https://docs.ropensci.org/biomartr/reference/biomart.md),
[`getDatasets()`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`getMarts()`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`organismBM()`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`organismFilters()`](https://docs.ropensci.org/biomartr/reference/organismFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# search for available datasets
getMarts()

# choose database (mart): ENSEMBL_MART_ENSEMBL
# and get a table of all available datasets from this BioMart database
head(getDatasets(mart = "ENSEMBL_MART_ENSEMBL"), 10)

# choose dataset: "hsapiens_gene_ensembl"
head(getAttributes(mart = "ENSEMBL_MART_ENSEMBL",
                   dataset = "hsapiens_gene_ensembl") , 5)
} # }
```
