# Retrieve ENSEMBL info file

Retrieve species and genome information from
http://rest.ensembl.org/info/species?content-type=application/json/.

## Usage

``` r
getENSEMBLInfo(update = FALSE, divisions = ensembl_divisions())
```

## Arguments

- update:

  logical, default FALSE. If TRUE, update cached list, if FALSE use
  existing cache (if it exists). For cache location see
  [`cachedir()`](https://docs.ropensci.org/biomartr/reference/cachedir.md)

- divisions:

  character, name of divisions to check, default is all from
  [`ensembl_divisions()`](https://docs.ropensci.org/biomartr/reference/ensembl_divisions.md).
  If NULL, also all is used.

## Value

a tibble table storing info for all available ENSEMBL divisions.

## See also

[`ensembl_divisions`](https://docs.ropensci.org/biomartr/reference/ensembl_divisions.md),
[`get.ensembl.info`](https://docs.ropensci.org/biomartr/reference/get.ensembl.info.md),
[`getKingdomAssemblySummary`](https://docs.ropensci.org/biomartr/reference/getKingdomAssemblySummary.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# look at available divisions
ensembl_divisions()
# retrieve information for all ENSEMBL divisions at once
test <- getENSEMBLInfo()
test
# retrieve information for a particular ENSEMBL division (e.g. EnsemblVertebrates)
test_vertebrates <- get.ensembl.info(update = TRUE, division = "EnsemblVertebrates")
test_vertebrates
} # }
```
