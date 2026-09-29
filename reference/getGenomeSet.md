# Genome Retrieval of multiple species

Main genome retrieval function for a set of organism of interest. By
specifying the scientific names of the organisms of interest the
corresponding fasta-files storing the genome of the organisms of
interest will be downloaded and stored locally. Genome files can be
retrieved from several databases.

## Usage

``` r
getGenomeSet(
  db = "refseq",
  organisms,
  reference = FALSE,
  release = NULL,
  skip_bacteria = TRUE,
  gunzip = TRUE,
  update = FALSE,
  path = "set_genomes",
  assembly_type = "toplevel",
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

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- update:

  logical, default FALSE. Updated backend cached files needed. Usually
  keep this false, to make ut run much faster. Only set to TRUE, if you
  believe you cache is outdated (Species only exist in newest release
  etc)

- path:

  a character string specifying the location (a folder) in which the
  corresponding genomes shall be stored. Default is `path` =
  `"set_genomes"`.

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

Other getBioSet:
[`getBioSet()`](https://docs.ropensci.org/biomartr/reference/getBioSet.md),
[`getCDSSet()`](https://docs.ropensci.org/biomartr/reference/getCDSSet.md),
[`getCollectionSet()`](https://docs.ropensci.org/biomartr/reference/getCollectionSet.md),
[`getGFFSet()`](https://docs.ropensci.org/biomartr/reference/getGFFSet.md),
[`getProteomeSet()`](https://docs.ropensci.org/biomartr/reference/getProteomeSet.md),
[`getRNASet()`](https://docs.ropensci.org/biomartr/reference/getRNASet.md)

Other genome:
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`read_genome()`](https://docs.ropensci.org/biomartr/reference/read_genome.md)

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
