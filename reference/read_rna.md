# Import RNA as Biostrings or data.table object

This function reads an organism specific RNA stored in a defined file
format.

## Usage

``` r
read_rna(file, format = "fasta", obj.type = "Biostrings", ...)
```

## Arguments

- file:

  a character string specifying the path to the file storing the RNA.

- format:

  a character string specifying the file format used to store the
  genome, e.g. `format = "fasta"` (default) or `format = "gbk"`.

- obj.type:

  a character string specifying the object stype in which the genomic
  sequence shall be represented. Either as `obj.type = "Biostrings"`
  (default) or as `obj.type = "data.table"`.

- ...:

  additional arguments that are used by
  [`read.fasta`](https://rdrr.io/pkg/seqinr/man/read.fasta.html).

## Value

A data.table storing the gene id in the first column and the
corresponding sequence as string in the second column.

## Details

This function takes a string specifying the path to the RNA file of
interest as first argument. It is possible to read in different proteome
file standards such as *fasta* or *genebank*.

## See also

Other rna:
[`getRNA()`](https://docs.ropensci.org/biomartr/reference/getRNA.md),
[`getRNASet()`](https://docs.ropensci.org/biomartr/reference/getRNASet.md)

Other readers:
[`read_cds()`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`read_genome()`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_gff()`](https://docs.ropensci.org/biomartr/reference/read_gff.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md)

## Author

Hajk-Georg Drost
