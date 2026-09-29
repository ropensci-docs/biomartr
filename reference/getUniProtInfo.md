# Get uniprot info from organism

Get uniprot info from organism

## Usage

``` r
getUniProtInfo(organism, path = cachedir(), update = TRUE)
```

## Arguments

- organism:

  character, name of organism

- path:

  path at which the info file shall be stored locally.

- update:

  shall the internal
  [`cachedir`](https://docs.ropensci.org/biomartr/reference/cachedir.md)
  file be deleted and the info file freshly downloaded from the UniProt
  API?
