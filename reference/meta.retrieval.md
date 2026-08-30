# Perform Meta-Genome Retrieval

Download genomes, proteomes, cds, gff, rna, or assembly stats files of
all species within a kingdom of life.

## Usage

``` r
meta.retrieval(
  db = "refseq",
  kingdom,
  group = NULL,
  type = "genome",
  restart_at_last = TRUE,
  max_species = NULL,
  reference = FALSE,
  combine = FALSE,
  path = kingdom,
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

- kingdom:

  a character string specifying the kingdom of the organisms of
  interest, e.g.

  - For `NCBI RefSeq / Genbank`:

    - `kingdom = "archaea"`

    - `kingdom = "bacteria"`

    - `kingdom = "fungi"`

    - `kingdom = "invertebrate"`

    - `kingdom = "plant"`

    - `kingdom = "protozoa"`

    - `kingdom = "viral"`

    - `kingdom = "vertebrate_mammalian"`

    - `kingdom = "vertebrate_other"`

  - For `ENSEMBL`:

    - `kingdom = "EnsemblVertebrates"`

    - `kingdom = "EnsemblPlants"`

    - `kingdom = "EnsemblFungi"`

    - `kingdom = "EnsemblMetazoa"`

    - `kingdom = "EnsemblBacteria"`

    - `kingdom = "EnsemblProtists"`

  Available kingdoms can be retrieved with
  [`getKingdoms`](https://docs.ropensci.org/biomartr/reference/getKingdoms.md).

- group:

  only species belonging to this subgroup will be downloaded. Groups can
  be retrieved with
  [`getGroups`](https://docs.ropensci.org/biomartr/reference/getGroups.md).

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

- restart_at_last:

  a logical value indicating whether or not `meta.retrieval` should pick
  up at the last species when re-running the function.

  - If `restart_at_last = TRUE` (Default) then `meta.retrieval` will
    skip all organisms that are already present in the folder and will
    start downloading all remaining species. However, this way
    `meta.wretrieval` will not be able to check whether already
    downloaded organism files are corrupted or not by checking the md5
    checksum.

  - If `restart_at_last = FALSE` then `meta.retrieval` will start from
    the beginning and crawl through already downloaded organism files
    and check whether already downloaded organism files are corrupted or
    not by checking the md5 checksum. After checking existing files the
    function will start downloading all remaining organisms.

- max_species:

  NULL, else numeric, defining maximum number of species to use. If
  number specified is higher than total species in group, it will use
  the group size.

- reference:

  a logical value indicating whether or not a genome shall be downloaded
  if it isn't marked in the database as either a reference genome or a
  representative genome. Options are:

  - `reference = FALSE` (Default): all organisms (reference,
    representative, and non-representative genomes) are downloaded.

  - `reference = TRUE`: organisms that are downloaded must be either a
    reference or representative genome. Thus, most genomes which are
    usually non-reference genomes will not be downloaded.

- combine:

  just in case `type = "assemblystats"` is specified, shall assemby
  stats of individual species be imported and combined to a
  [`data.frame`](https://rdrr.io/r/base/data.frame.html)?

- path:

  path to the folder in which downloaded genomes shall be stored. By
  default the kingdom name is used to name the output folder.

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

This function aims to perform bulk retrieval of the genomes, proteomes,
cds, etc. of species that belong to the same kingdom of life or to the
same subgroup.

## See also

Other meta_retrival:
[`meta.retrieval.all()`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.all.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# get all available kingdoms for refseq
getKingdoms(db = "refseq")
# download all vertebrate genomes from refseq
meta.retrieval(kingdom = "vertebrate_mammalian",
               db = "refseq",
               type = "genome")

# get all available kingdoms for genbank
getKingdoms(db = "genbank")
# download all vertebrate genomes from genbank
meta.retrieval(kingdom = "vertebrate_mammalian",
               db = "genbank",
               type = "genome")


# In case users do not wish to retrieve genomes from an entire kingdom,
# but rather from a subgoup (e.g. from species belonging to the
# Gammaproteobacteria class, a subgroup of the bacteria kingdom),
# they can use the following workflow"
# First, users can again consult the getKingdoms() function to retrieve
# kingdom information.
getKingdoms(db = "refseq")

# In this example, we will choose the bacteria kingdom.
# Now, the getGroups() function allows users to obtain available
# subgroups of the bacteria kingdom.
getGroups(db = "refseq", kingdom = "bacteria")

# Now we choose the group Gammaproteobacteria and specify
# the group argument in the meta.retrieval() function
meta.retrieval(kingdom = "bacteria",
   group = "Gammaproteobacteria",
   db = "refseq",
   type = "genome")
} # }
```
