# Import Proteome as Biostrings or data.table object

This function reads an organism specific proteome stored in a defined
file format.

## Usage

``` r
read_proteome(file, format = "fasta", obj.type = "Biostrings", ...)
```

## Arguments

- file:

  a character string specifying the path to the file storing the
  proteome.

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

Either a `Biostrings` or `data.table` object.

## Details

This function takes a string specifying the path to the proteome file of
interest as first argument.

It is possible to read in different proteome file standards such as
*fasta* or *genebank*.

## See also

Other readers:
[`read_cds()`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`read_genome()`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_gff()`](https://docs.ropensci.org/biomartr/reference/read_gff.md),
[`read_rna()`](https://docs.ropensci.org/biomartr/reference/read_rna.md)

Other proteome:
[`getProteome()`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getProteomeSet()`](https://docs.ropensci.org/biomartr/reference/getProteomeSet.md)

## Author

Hajk-Georg Drost
