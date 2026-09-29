# Retrieve available groups for a kingdom of life (only available for NCBI RefSeq and NCBI Genbank)

A short list of available groups for a kingdom of life.

## Usage

``` r
getGroups(db = "refseq", kingdom)
```

## Arguments

- db:

  a character string specifying the database from which the genome shall
  be retrieved:

  - `db = "refseq"`

  - `db = "genbank"`

  Default is `db = "refseq"`.

- kingdom:

  a character string specifying for which kingdom of life groups shall
  be retrieved. See
  [`getKingdoms`](https://docs.ropensci.org/biomartr/reference/getKingdoms.md)
  for details.

## See also

[`meta.retrieval`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.md),
[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getKingdoms`](https://docs.ropensci.org/biomartr/reference/getKingdoms.md)

## Author

Hajk-Georg Drost

## Examples

``` r
# get possible kigdom names
getKingdoms(db = "refseq")
#> [1] "archaea"              "bacteria"             "fungi"               
#> [4] "invertebrate"         "plant"                "protozoa"            
#> [7] "vertebrate_mammalian" "vertebrate_other"     "viral"               
if (FALSE) { # \dontrun{
# retrieve subgroups for vertebrate_mammalian available from refseq
getGroups(db = "refseq", kingdom = "vertebrate_mammalian")

# get possible kigdom names
getKingdoms(db = "genbank")
# retrieve subgroups for vertebrate_mammalian available from genbank
getGroups(db = "genbank", kingdom = "vertebrate_mammalian")
} # }
```
