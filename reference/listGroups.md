# List number of available genomes in each taxonomic group

Users can retrieve the available number of sequenced genomes per group.
Only available for `db = "refseq"` and `db = "genbank"`.

## Usage

``` r
listGroups(db = "refseq", kingdom = "all", details = FALSE)
```

## Arguments

- db:

  a character string specifying the database for which genome
  availability shall be checked. Available options are:

  - `db = "refseq"`

  - `db = "genbank"`

- kingdom:

  a kingdom specification retrieved by
  [`getKingdoms`](https://docs.ropensci.org/biomartr/reference/getKingdoms.md).

- details:

  shall all species corresponding to the specified `kingdom` be
  returned? Default is `details = FALSE`.

## See also

[`listGenomes`](https://docs.ropensci.org/biomartr/reference/listGenomes.md),
[`is.genome.available`](https://docs.ropensci.org/biomartr/reference/is.genome.available.md),
[`listKingdoms`](https://docs.ropensci.org/biomartr/reference/listKingdoms.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# retrieve a list of available kingdoms for RefSeq
getKingdoms(db = "refseq")
# [1] "archaea"              "bacteria"             "fungi"                "invertebrate"         "plant"               
# [6] "protozoa"             "vertebrate_mammalian" "vertebrate_other"     "viral"  
# example for refseq
listGroups(db = "refseq")
# example for genbank
listGroups(db = "genbank")
### in case groups should be specified by kingdom
# first, retrieve available kingdom names
listKingdoms()
# now we choose kingdom "bacteria"
listGroups(db = "refseq", kingdom = "bacteria")
# or
listGroups(db = "genbank", kingdom = "bacteria")
} # }
```
