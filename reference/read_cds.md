# Import CDS as Biostrings or data.table object

This function reads an organism specific CDS stored in a defined file
format.

## Usage

``` r
read_cds(
  file,
  format = "fasta",
  obj.type = "Biostrings",
  delete_corrupt = FALSE,
  ...
)
```

## Arguments

- file:

  a character string specifying the path to the file storing the CDS.

- format:

  a character string specifying the file format used to store the
  genome, e.g. `format = "fasta"` (default) or `format = "gbk"`.

- obj.type:

  a character string specifying the object stype in which the genomic
  sequence shall be represented. Either as `obj.type = "Biostrings"`
  (default) or as `obj.type = "data.table"`.

- delete_corrupt:

  a logical value specifying whether potential CDS sequences that cannot
  be divided by 3 shall be be excluded from the the dataset. Default is
  `delete_corrupt = FALSE`.

- ...:

  additional arguments that are used by
  [`read.fasta`](https://rdrr.io/pkg/seqinr/man/read.fasta.html).

## Value

A data.table storing the gene id in the first column and the
corresponding sequence as string in the second column.

## Details

The `read.cds` function takes a string specifying the path to the cds
file of interest as first argument.

It is possible to read in different proteome file standards such as
*fasta* or *genebank*.

CDS stored in fasta files can be downloaded from
http://www.ensembl.org/info/data/ftp/index.html.

## See also

Other cds:
[`getCDS()`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getCDSSet()`](https://docs.ropensci.org/biomartr/reference/getCDSSet.md)

Other readers:
[`read_genome()`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_gff()`](https://docs.ropensci.org/biomartr/reference/read_gff.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md),
[`read_rna()`](https://docs.ropensci.org/biomartr/reference/read_rna.md)

## Author

Hajk-Georg Drost
