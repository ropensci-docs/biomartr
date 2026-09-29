# Generic Bio data set extractor

Usually you want to use one of the specific set extractors

## Usage

``` r
getBioSet(
  db = "refseq",
  organisms,
  set_type,
  reference = FALSE,
  release = NULL,
  gunzip = TRUE,
  update = FALSE,
  skip_bacteria = TRUE,
  path = paste0("set_", toupper(set_type)),
  remove_annotation_outliers = FALSE,
  assembly_type = "toplevel",
  format = "gff3",
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

- organisms:

  a character vector storing the names of the organisms than shall be
  retrieved. There are three available options to characterize an
  organism:

- set_type:

  the biological sequence type that shall be retrieved. Available
  options are

  - `set_type = "genome"`

  - `set_type = "proteome"`

  - `set_type = "cds"`

  - `set_type = "gff"`

  - `set_type = "rna"`

  - `set_type = "assembly_stats"`

  - `set_type = "repeat_masker"`

  - `set_type = "collection"` (all the others)

- reference:

  a logical value indicating whether or not a genome shall be a
  candidate for downloaded if it isn't marked in the database as either
  a reference genome or a representative genome. This is helpful if you
  don't want to allow "partial genomes" etc.

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- update:

  logical, default FALSE. Updated backend cached files needed. Usually
  keep this false, to make ut run much faster. Only set to TRUE, if you
  believe you cache is outdated (Species only exist in newest release
  etc)

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- path:

  character, default location is paste0("set\_", toupper(set_type))

- remove_annotation_outliers:

  shall outlier lines be removed from the input `annotation_file`? If
  yes, then the initial `annotation_file` will be overwritten and the
  removed outlier lines will be stored at
  [`tempdir`](https://rdrr.io/r/base/tempfile.html) for further
  exploration.

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

- format:

  character, For annotation: default: "gff3", alternative "gtf" for
  ensembl.  
  For assembly_stats, alternatives "download" / "txt" (download only),
  "import" import dataset.

- mute_citation:

  logical, default FALSE, indicating whether citation message should be
  muted.

## Value

character vector, the file path to the downloaded genomes,  
The returned character vector has names as either:  
- 'new' (file was downloaded now)  
- 'old' files did already exist)

## Details

Fetching of assembly / sequence data is done by fetching an overview
file from metadata of given database:  
For NCBI (refseq/genbank):  
Internally this function loads the the overview.txt file from NCBI:

refseq: ftp.ncbi.nlm.nih.gov/genomes/refseq/

genbank: ftp.ncbi.nlm.nih.gov/genomes/genbank/

It will then create a directory relative to file type wanted, if you get
fasta genomes it will be \_ncbi_downloads/genomes' etc. In case the
corresponding fasta file already exists within the
'\_ncbi_downloads/genomes' folder and is accessible within the
workspace, no download process will be performed. For other file types
the same rule applies.  

For ensembl it fetches overview per type from the rest API:

ensembl: https://rest.ensembl.org

## See also

[`getBio`](https://docs.ropensci.org/biomartr/reference/getBio.md)

Other getBioSet:
[`getCDSSet()`](https://docs.ropensci.org/biomartr/reference/getCDSSet.md),
[`getCollectionSet()`](https://docs.ropensci.org/biomartr/reference/getCollectionSet.md),
[`getGFFSet()`](https://docs.ropensci.org/biomartr/reference/getGFFSet.md),
[`getGenomeSet()`](https://docs.ropensci.org/biomartr/reference/getGenomeSet.md),
[`getProteomeSet()`](https://docs.ropensci.org/biomartr/reference/getProteomeSet.md),
[`getRNASet()`](https://docs.ropensci.org/biomartr/reference/getRNASet.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
getBioSet("refseq", organisms = c("Arabidopsis thaliana",
                                  "Arabidopsis lyrata",
                                  "Capsella rubella"),
                                  set_type = "cds")
} # }
```
