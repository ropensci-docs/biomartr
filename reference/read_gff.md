# Import GFF File

This function reads an organism specific CDS stored in a defined file
format.

## Usage

``` r
read_gff(file)
```

## Arguments

- file:

  a character string specifying the path to the file storing the CDS.

## Value

Either a `Biostrings` or `data.table` object.

## Details

This function takes a string specifying the path to the GFF file of
interest (e.g. the path returned by
[`getGFF`](https://docs.ropensci.org/biomartr/reference/getGFF.md)).

## See also

Other gff:
[`getGFF()`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getGFFSet()`](https://docs.ropensci.org/biomartr/reference/getGFFSet.md)

Other readers:
[`read_cds()`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`read_genome()`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md),
[`read_rna()`](https://docs.ropensci.org/biomartr/reference/read_rna.md)

## Author

Hajk-Georg Drost
