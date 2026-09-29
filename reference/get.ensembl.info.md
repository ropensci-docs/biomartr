# Helper function to retrieve species information from the ENSEMBL API

This function interfaces with the ENSEMBL API
(https://rest.ensembl.org/info/species?content-type=application/json)
and internally stores the output to use this information for subsequent
retrieval function calls.

## Usage

``` r
get.ensembl.info(update = FALSE, division)
```

## Arguments

- update:

  logical, default FALSE. If TRUE, force re-download of info.

- division:

  the ENSEMBL database (division) for which information shall be
  retrieved (available options can be obtained with
  [`ensembl_divisions`](https://docs.ropensci.org/biomartr/reference/ensembl_divisions.md)).

## See also

[`ensembl_divisions`](https://docs.ropensci.org/biomartr/reference/ensembl_divisions.md),
[`getKingdomAssemblySummary`](https://docs.ropensci.org/biomartr/reference/getKingdomAssemblySummary.md),
[`getENSEMBLInfo`](https://docs.ropensci.org/biomartr/reference/getENSEMBLInfo.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# Look at available ENSEMBL division options
ensembl_divisions()
# Retrieve available information for EnsemblVertebrates
example <- get.ensembl.info(division = "EnsemblVertebrates")
example
# Update information file stored in the tempdir() folder.
example_update <- get.ensembl.info(division = "EnsemblVertebrates", update = TRUE)
example_update
} # }
```
