# Retrieve summary statistics for a coding sequence (CDS) file

A summary statistics of specific CDS features is returned.

## Usage

``` r
summary_cds(file, organism)
```

## Arguments

- file:

  file path to a CDS file in `fasta` format.

- organism:

  character string specifying the organism at hand.

## Details

The summary statistics include:

- `total_seqs`:

- `nnn_abs`: The total number of NNN's (over all
  chromosomes/scaffolds/contigs) in all coding sequences combined

- `nnn_perc`: The percentage (relative frequency) of NNN's (over all
  chromosomes/scaffolds/contigs) compared to the total number of
  nucleotides of all coding sequences

## See also

[`getCollection`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`read_cds`](https://docs.ropensci.org/biomartr/reference/read_cds.md),
[`summary_genome`](https://docs.ropensci.org/biomartr/reference/summary_genome.md)

## Author

Hajk-Georg Drost
