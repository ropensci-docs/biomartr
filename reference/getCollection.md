# Retrieve a Collection: Genome, Proteome, CDS, RNA, GFF, Repeat Masker, AssemblyStats

Main collection retrieval function for an organism of interest. By
specifying the scientific name of an organism of interest a collection
consisting of the genome file, proteome file, CDS file, RNA file, GFF
file, Repeat Masker file, AssemblyStats file of the organism of interest
can be downloaded and stored locally. Collections can be retrieved from
several databases. For full set of collection elements, see:
biomartr:::supported_biotypes(db)

## Usage

``` r
getCollection(
  db = "refseq",
  organism,
  reference = TRUE,
  skip_bacteria = TRUE,
  release = NULL,
  assembly_type = "toplevel",
  analyse_genome = FALSE,
  remove_annotation_outliers = FALSE,
  gunzip = FALSE,
  path = file.path("_db_downloads", "collections"),
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

- organism:

  Organism selector id, there are three options to characterize an
  organism:

  - by `scientific name`: e.g. `organism = "Homo sapiens"`

  - by `database specific accession identifier`: e.g.
    `organism = "GCF_000001405.37"` (= NCBI RefSeq identifier for
    `Homo sapiens`)

  - by `taxonomic identifier from NCBI Taxonomy`: e.g.
    `organism = "9606"` (= taxid of `Homo sapiens`)

- reference:

  a logical value indicating whether or not a genome shall be a
  candidate for downloaded if it isn't marked in the database as either
  a reference genome or a representative genome. This is helpful if you
  don't want to allow "partial genomes" etc.

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

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

- analyse_genome:

  logical, default FALSE. If TRUE, get general genome statistics like gc
  content etc. For more details, see ?summary_genome

- remove_annotation_outliers:

  shall outlier lines be removed from the input `annotation_file`? If
  yes, then the initial `annotation_file` will be overwritten and the
  removed outlier lines will be stored at
  [`tempdir`](https://rdrr.io/r/base/tempfile.html) for further
  exploration.

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- path:

  a character string specifying the location (a folder) in which the
  corresponding collection shall be stored. Default is `path` =
  `file.path("_db_downloads","collections")`.

- mute_citation:

  logical, default FALSE, indicating whether citation message should be
  muted.

## Value

File path to downloaded genome.

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

Other getBio:
[`getBio()`](https://docs.ropensci.org/biomartr/reference/getBio.md),
[`getCDS()`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getGFF()`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome()`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getRNA()`](https://docs.ropensci.org/biomartr/reference/getRNA.md)

Other collection:
[`getCollectionSet()`](https://docs.ropensci.org/biomartr/reference/getCollectionSet.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download the collection of Homo sapiens from refseq
# and store the corresponding genome file in '_ncbi_downloads/collection'
 Hsap_collection <- getCollection( db       = "refseq",
             organism = "Homo sapiens",
             path = file.path("_db_downloads","collections"))
# download the collection of Homo sapiens from genbank
# and store the corresponding genome file in '_ncbi_downloads/collection'
 Hsap_collection <- getCollection( db       = "genbank",
             organism = "Homo sapiens",
             path = file.path("_db_downloads","collections"))
# download the collection of Homo sapiens from ensembl
# and store the corresponding genome file in '_ncbi_downloads/collection'
 Hsap_collection <- getCollection( db       = "ensembl",
             organism = "Homo sapiens",
             path = file.path("_db_downloads","collections"))
} # }
```
