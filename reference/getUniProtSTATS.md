# Retrieve UniProt Database Information File (STATS)

The UniProt stores a `STATS` file to summarise all available information
for their reference proteomes. Users can now download this file and
process it with `biomartr`.

## Usage

``` r
getUniProtSTATS(update = FALSE)
```

## Arguments

- update:

  shall the internal
  [`cachedir`](https://docs.ropensci.org/biomartr/reference/cachedir.md)
  file be deleted and the `STATS` file freshly downloaded from the
  UniProt FTP servers?

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# retrieve STATS file from UniProt
uniprot_info <- getUniProtSTATS(update = TRUE)
# look at results
uniprot_info
} # }
```
