# Import Genome Assembly Stats File

This function reads an organism specific Genome Assembly Stats file that
was retrieved with
[`getAssemblyStats`](https://docs.ropensci.org/biomartr/reference/getAssemblyStats.md).

## Usage

``` r
read_assemblystats(file, type = "raw", organism = NULL)
```

## Arguments

- file:

  a character string specifying the path to the file storing the Genome
  Assembly Stats file.

- type:

  a tibble object, either `type = "raw"` to import the entire genome
  assembly stats file or `type = "stats"` to import overall statistics
  including all chromosomes, mitochondria and plastids.

- organism:

  character, if not NULL, appends a column left side called 'species'
  with this value.

## Details

This function takes a string specifying the path to the Genome Assembly
Stats file of interest (e.g. the path returned by
[`getAssemblyStats`](https://docs.ropensci.org/biomartr/reference/getAssemblyStats.md))
and imports it.

## See also

[`getAssemblyStats`](https://docs.ropensci.org/biomartr/reference/getAssemblyStats.md),
[`read_genome`](https://docs.ropensci.org/biomartr/reference/read_genome.md),
[`read_proteome`](https://docs.ropensci.org/biomartr/reference/read_proteome.md),
[`read_cds`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`read_gff`](https://docs.ropensci.org/biomartr/reference/read_gff.md)

## Author

Hajk-Georg Drost
