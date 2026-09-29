# Perform Meta-Genome Retrieval of all organisms in all kingdoms of life

Download genomes, proteomes, cds, gff, rna, or assembly stats files of
individual species of all kingdoms of life.

## Usage

``` r
meta.retrieval.all(
  db = "refseq",
  type = "genome",
  reference = FALSE,
  release = NULL,
  remove_annotation_outliers = FALSE,
  analyse_genome = FALSE,
  assembly_type = "toplevel",
  skip_bacteria = FALSE,
  mute_citation = FALSE
)
```

## Arguments

- db:

  a character string specifying the database from which the genome shall
  be retrieved:

  - `db = "refseq"`

  - `db = "genbank"`

  - `db = "ensembl"`

- type:

  type of sequences that shall be retrieved. Options are:

  - `type = "genome"` : (for genome assembly retrieval; see also
    [`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md)),

  - `type = "proteome"` : (for proteome retrieval; see also
    [`getProteome`](https://docs.ropensci.org/biomartr/reference/getProteome.md)),

  - `type = "cds"` : (for coding sequence retrieval; see also
    [`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md)),

  - `type = "gff"` : (for annotation file retrieval in gff format; see
    also
    [`getGFF`](https://docs.ropensci.org/biomartr/reference/getGFF.md)),

  - `type = "gtf"` : (for annotation file retrieval in gtf format (only
    for ensembl and ensemblgenomes); see also
    [`getGTF`](https://docs.ropensci.org/biomartr/reference/getGTF.md))

  - `type = "rna"` : (for RNA file retrieval in fasta format; see also
    [`getRNA`](https://docs.ropensci.org/biomartr/reference/getRNA.md)),

  - `type = "repeat_masker" or "rm"` : (for Repeat Masker output file
    retrieval; see also
    [`getRepeatMasker`](https://docs.ropensci.org/biomartr/reference/getRepeatMasker.md)),

  - `type = "assembly_stats" or "assemblystats"` : (for genome assembly
    quality stats file retrieval; see also
    [`getAssemblyStats`](https://docs.ropensci.org/biomartr/reference/getAssemblyStats.md)).

- reference:

  a logical value indicating whether or not a genome shall be downloaded
  if it isn't marked in the database as either a reference genome or a
  representative genome. Options are:

  - `reference = FALSE` (Default): all organisms (reference,
    representative, and non-representative genomes) are downloaded.

  - `reference = TRUE`: organisms that are downloaded must be either a
    reference or representative genome. Thus, most genomes which are
    usually non-reference genomes will not be downloaded.

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

- remove_annotation_outliers:

  shall outlier lines be removed from the input `annotation_file`? If
  yes, then the initial `annotation_file` will be overwritten and the
  removed outlier lines will be stored at
  [`tempdir`](https://rdrr.io/r/base/tempfile.html) for further
  exploration.

- analyse_genome:

  logical, default FALSE. If TRUE, get general genome statistics like gc
  content etc. For more details, see ?summary_genome

- assembly_type:

  character, default c("primary_assembly", "toplevel"). Used for ensembl
  only, specifies the genome assembly type. Searches for both primary
  and toplevel, and if both are found, uses the first by order (so
  primary is prioritized by default). The Primary assembly should
  usually be used if it exists. The "primary assembly" contains all the
  top-level sequence regions, excluding alternative haplotypes and
  patches. If the primary assembly file is not present for a species
  (only defined for standard model organisms), that indicates that there
  were no haplotype/patch regions, and in such cases, the 'toplevel file
  is used. For more details see: [ensembl
  tutorial](https://grch37.ensembl.org/info/genome/genebuild/assembly.html)

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- mute_citation:

  logical, default FALSE, indicating whether citation message should be
  muted.

## Value

a character vector storing the file paths of the retrieved files.

## Details

This function aims to perform bulk retrieval of all genomes of species
for all kingdoms of life.

## See also

Other meta_retrival:
[`meta.retrieval()`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download all genomes from refseq
meta.retrieval.all(db = "refseq", type = "genome")
# download all vertebrate genomes from genbank
meta.retrieval.all(db = "genbank", type = "genome")
# download all vertebrate genomes from ensemblgenomes
meta.retrieval.all(db = "genbank", type = "ensemblgenomes")
} # }
```
