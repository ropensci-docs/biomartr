# Import Repeat Masker output file

This function reads an organism specific Repeat Masker output file.

## Usage

``` r
read_rm(file)
```

## Arguments

- file:

  a character string specifying the path to the file storing the Repeat
  Masker output (e.g. retrieved with
  [`getRepeatMasker`](https://docs.ropensci.org/biomartr/reference/getRepeatMasker.md)).

## Details

This function takes a string specifying the path to the Repeat Masker
output file of interest as first argument.

## See also

[`getRepeatMasker`](https://docs.ropensci.org/biomartr/reference/getRepeatMasker.md),
[`read_genome`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_proteome`](https://docs.ropensci.org/biomartr/reference/read_proteome.md),
[`read_gff`](https://docs.ropensci.org/biomartr/reference/read_gff.md),
[`read_rna`](https://docs.ropensci.org/biomartr/reference/read_rna.md)

## Author

Hajk-Georg Drost
