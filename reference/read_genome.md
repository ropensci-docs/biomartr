# Import Genome Assembly as Biostrings or data.table object

This function reads an organism specific genome stored in a defined file
format.

## Usage

``` r
read_genome(file, format = "fasta", obj.type = "Biostrings", ...)
```

## Arguments

- file:

  a character string specifying the path to the file storing the genome.

- format:

  a character string specifying the file format used to store the
  genome, e.g. `format = "fasta"` (default) or `format = "gbk"`.

- obj.type:

  a character string specifying the object stype in which the genomic
  sequence shall be represented. Either as `obj.type = "Biostrings"`
  (default) or as `obj.type = "data.table"`.

- ...:

  additional arguments that are used by the
  [`read.fasta`](https://rdrr.io/pkg/seqinr/man/read.fasta.html)
  function.

## Value

Either a `Biostrings` or `data.table` object.

## Details

This function takes a string specifying the path to the genome file of
interest as first argument (e.g. the path returned by
[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md)).

## See also

Other genome:
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getGenomeSet()`](https://docs.ropensci.org/biomartr/reference/getGenomeSet.md)

Other readers:
[`read_cds()`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`read_gff()`](https://docs.ropensci.org/biomartr/reference/read_gff.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md),
[`read_rna()`](https://docs.ropensci.org/biomartr/reference/read_rna.md)

## Author

Hajk-Georg Drost
