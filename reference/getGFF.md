# Genome Annotation Retrieval (GFF3)

Main retrieval function for GFF files of an organism of interest. By
specifying the scientific name of an organism of interest the
corresponding gff file storing the annotation for the organism of
interest can be downloaded and stored locally. GFF files can be
retrieved from several databases.

## Usage

``` r
getGFF(
  db = "refseq",
  organism,
  reference = FALSE,
  skip_bacteria = TRUE,
  release = NULL,
  gunzip = FALSE,
  remove_annotation_outliers = FALSE,
  path = file.path("_ncbi_downloads", "annotation"),
  mute_citation = FALSE,
  format = "gff3"
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

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- remove_annotation_outliers:

  shall outlier lines be removed from the input `annotation_file`? If
  yes, then the initial `annotation_file` will be overwritten and the
  removed outlier lines will be stored at
  [`tempdir`](https://rdrr.io/r/base/tempfile.html) for further
  exploration.

- path:

  a character string specifying the location (a folder) in which the
  corresponding annotation file shall be stored. Default is
  `path = file.path("_ncbi_downloads","annotation")`.

- mute_citation:

  logical, default FALSE, indicating whether citation message should be
  muted.

- format:

  character, For annotation: default: "gff3", alternative "gtf" for
  ensembl.  
  For assembly_stats, alternatives "download" / "txt" (download only),
  "import" import dataset.

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
[`getCollection()`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome()`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getRNA()`](https://docs.ropensci.org/biomartr/reference/getRNA.md)

Other gff:
[`getGFFSet()`](https://docs.ropensci.org/biomartr/reference/getGFFSet.md),
[`read_gff()`](https://docs.ropensci.org/biomartr/reference/read_gff.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# Simple and small yeast download from refseq
 getGFF( db       = "refseq", organism = "Saccharomyces cerevisiae",
  path = tempdir(), mute_citation = TRUE)
# download the annotation of Arabidopsis thaliana from refseq
# and store the corresponding genome file in '_ncbi_downloads/annotation'
Athal_gff <- getGFF( db       = "refseq",
               organism = "Arabidopsis thaliana",
               path = file.path("_ncbi_downloads","annotation"),
               remove_annotation_outliers = TRUE)
Athal_gff_import <- read_gff(Athal_gff)


# download the genome of Arabidopsis thaliana from genbank
# and store the corresponding genome file in '_ncbi_downloads/annotation'
Athal_gff <- getGFF( db       = "genbank",
               organism = "Arabidopsis thaliana",
               path = file.path("_ncbi_downloads","annotation"),
               remove_annotation_outliers = TRUE)
Athal_gff_import <- read_gff(Athal_gff)

# download the genome of Homo sapiens from ensembl
# and store the corresponding genome file in '_ncbi_downloads/annotation'
Hsap_gff <- getGFF( db       = "ensembl",
               organism = "Homo sapiens",
               path = file.path("_ncbi_downloads","annotation"),
               remove_annotation_outliers = TRUE)
Hsap_gff_import <- read_gff(Hsap_gff)

} # }
```
