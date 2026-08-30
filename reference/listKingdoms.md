# List number of available genomes in each kingdom of life

Users can retrieve the available number of sequenced genomes per
kingdom.

## Usage

``` r
listKingdoms(db = "refseq")
```

## Arguments

- db:

  a character string specifying the database for which genome
  availability shall be checked, e.g. `db = "refseq"`, `db = "genbank"`,
  `db = "ensembl"`.

## See also

[`listGenomes`](https://docs.ropensci.org/biomartr/reference/listGenomes.md),
[`is.genome.available`](https://docs.ropensci.org/biomartr/reference/is.genome.available.md),
[`listGroups`](https://docs.ropensci.org/biomartr/reference/listGroups.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# list number of available genomes in refseq for each kingdom of life
listKingdoms(db = "refseq")
# example for genbank
listKingdoms(db = "genbank")
# example for ensembl
listKingdoms(db = "ensembl")
} # }
```
