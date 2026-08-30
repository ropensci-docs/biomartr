# Retrieve summary statistics for a genome assembly file

A summary statistics of specific genome features is generated. These
statistics are useful to assess the genome quality of retrieved genome
assemblies when performing comparative genomics tasks. This way, users
can assess whether or not patterns found based on genome comparisons
aren't just a technical artifact of differences in genome assembly
quality.

## Usage

``` r
summary_genome(file, organism)
```

## Arguments

- file:

  file path to a genome assembly file in `fasta` format.

- organism:

  character string specifying the organism at hand.

## Details

The summary statistics include:

- `genome_size_mbp`: Genome size in mega base pairs

- `n50_mbp`: The N50 contig size of the genome assembly in mega base
  pairs

- `n_seqs`: The number of chromosomes/scaffolds/contigs of the genome
  assembly file

- `n_nnn`: The absolute number of NNNs (over all chromosomes or
  scaffolds or contigs) in the genome assembly file

- `rel_nnn`: The percentage (relative frequency) of NNNs (over all
  chromosomes or scaffolds or contigs) compared to the total number of
  nucleotides in the genome assembly file

- `genome_entropy`: The `Shannon Entropy` of the genome assembly file
  (median entropy over all individual chromosome entropies)

- `n_gc`: The total number of GCs (over all chromosomes or scaffolds or
  contigs) in the genome assembly file

- `rel_gc`: The (relative frequency) of GCs (over all chromosomes or
  scaffolds or contigs) compared to the total number of nucleotides in
  the genome assembly file

## See also

[`summary_cds`](https://docs.ropensci.org/biomartr/reference/summary_cds.md),
[`getCollection`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`read_genome`](https://docs.ropensci.org/biomartr/reference/read_genome.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# retrieve genome from NCBI RefSeq
Sc <- biomartr::getGenome(db = "refseq", organism = "Saccharomyces cerevisiae")
# compute genome assembly summary statistics
Sc_genome_summary <- summary_genome(file = Sc, organism = "Saccharomyces cerevisiae")
# look at results
Sc_genome_summary
} # }
```
