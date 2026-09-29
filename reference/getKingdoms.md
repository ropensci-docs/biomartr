# Retrieve available kingdoms of life

A short list of available kingdoms of life

## Usage

``` r
getKingdoms(db = "refseq")
```

## Arguments

- db:

  a character string specifying the database from which the genome shall
  be retrieved: `db = "refseq"`, `db = "genbank"`, `db = "ensembl"`,
  `db = "ensemblgenomes"`. Default is `db = "refseq"`.

## See also

[`meta.retrieval`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.md),
[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getGroups`](https://docs.ropensci.org/biomartr/reference/getGroups.md)

## Author

Hajk-Georg Drost

## Examples

``` r
# retrieve kingdoms available from refseq
getKingdoms(db = "refseq")
#> [1] "archaea"              "bacteria"             "fungi"               
#> [4] "invertebrate"         "plant"                "protozoa"            
#> [7] "vertebrate_mammalian" "vertebrate_other"     "viral"               

# retrieve kingdoms available from genbank
getKingdoms(db = "genbank")
#> [1] "archaea"              "bacteria"             "fungi"               
#> [4] "invertebrate"         "plant"                "protozoa"            
#> [7] "vertebrate_mammalian" "vertebrate_other"    
```
