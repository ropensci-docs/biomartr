# Proteome retrieval of multiple species

Main proteome retrieval function for a set of organism of interest. By
specifying the scientific names of the organisms of interest the
corresponding fasta-files storing the proteome of the organisms of
interest will be downloaded and stored locally. proteome files can be
retrieved from several databases.

## Usage

``` r
getProteomeSet(
  db = "refseq",
  organisms,
  reference = FALSE,
  release = NULL,
  skip_bacteria = TRUE,
  gunzip = TRUE,
  update = FALSE,
  path = "set_proteomes",
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
  corresponding proteomes shall be stored. Default is `path` =
  `"set_proteomes"`.

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
[`getGenomeSet()`](https://docs.ropensci.org/biomartr/reference/getGenomeSet.md),
[`getRNASet()`](https://docs.ropensci.org/biomartr/reference/getRNASet.md)

Other proteome:
[`getProteome()`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download the proteomes of three different species at the same time
#### Database: NCBI RefSeq
file_paths <- getProteomeSet(db = "refseq", organisms = c("Arabidopsis thaliana",
                                      "Arabidopsis lyrata",
                                       "Capsella rubella"))
# look at file paths
file_paths

#### Database: NCBI Genbank
file_paths <- getProteomeSet(db = "genbank", organisms = c("Arabidopsis thaliana",
                                      "Arabidopsis lyrata",
                                       "Capsella rubella"))
# look at file paths
file_paths

# download the proteomes of three different species at the same time
#### Database: ENSEMBL
file_paths <- getProteomeSet(db = "ensembl", organisms = c("Homo sapiens",
                                      "Mus musculus",
                                       "Caenorhabditis elegans"))
# look at file paths
file_paths

# download the proteomes of three different species at the same time
#### Database: UniProt
file_paths <- getProteomeSet(db = "uniprot", organisms = c("Homo sapiens",
                                      "Mus musculus",
                                       "Caenorhabditis elegans"))
# look at file paths
file_paths
} # }
```
