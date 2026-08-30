# Proteome Retrieval

Main proteome retrieval function for an organism of interest. By
specifying the scientific name of an organism of interest the
corresponding fasta-file storing the proteome of the organism of
interest can be downloaded and stored locally. Proteome files can be
retrieved from several databases.

## Usage

``` r
getProteome(
  db = "refseq",
  organism,
  reference = TRUE,
  skip_bacteria = TRUE,
  release = NULL,
  gunzip = FALSE,
  update = TRUE,
  path = file.path("_ncbi_downloads", "proteomes"),
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

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- update:

  logical, default TRUE. (Uniprot only for now!) If species info file
  exists already, do not re download, makes it faster but the file can
  be old, i.e. no longer as complete as it could be.

- path:

  a character string specifying the location (a folder) in which the
  corresponding proteome shall be stored. Default is `path` =
  `file.path("_ncbi_downloads","proteomes")`.

- mute_citation:

  logical, default FALSE, indicating whether citation message should be
  muted.

## Value

File path to downloaded proteome.

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
[`getGFF()`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getRNA()`](https://docs.ropensci.org/biomartr/reference/getRNA.md)

Other proteome:
[`getProteomeSet()`](https://docs.ropensci.org/biomartr/reference/getProteomeSet.md),
[`read_proteome()`](https://docs.ropensci.org/biomartr/reference/read_proteome.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download the proteome of Arabidopsis thaliana from NCBI RefSeq
# and store the corresponding proteome file in '_ncbi_downloads/refseq/proteomes'
file_path <- getProteome( db       = "refseq",
             organism = "Arabidopsis thaliana",
             path     = file.path("_ncbi_downloads","refseq","proteomes") )
# import proteome into R session
Ath_proteome <- read_proteome(file_path, format = "fasta")

# download the proteome of Arabidopsis thaliana from NCBI Genbank
# and store the corresponding proteome file in '_ncbi_downloads/genbank/proteomes'
file_path <- getProteome( db       = "genbank",
             organism = "Arabidopsis thaliana",
             path     = file.path("_ncbi_downloads","genbank","proteomes") )
# import proteome into R session
Ath_proteome <- read_proteome(file_path, format = "fasta")

# and store the corresponding proteome file in '_downloads/uniprot/proteomes'
file_path <- getProteome( db       = "uniprot",
             organism = "Arabidopsis thaliana",
             path     = file.path("_downloads","uniprot","proteomes") )
# import proteome into R session
Ath_proteome <- read_proteome(file_path, format = "fasta")

# download the proteome of Arabidopsis thaliana from ENSEMBL
# and store the corresponding proteome file in '_downloads/ensembl/proteomes'
file_path <- getProteome( db       = "ensembl",
             organism = "Arabidopsis thaliana",
             path     = file.path("_downloads","ensembl","proteomes") )
# import proteome into R session
Ath_proteome <- read_proteome(file_path, format = "fasta")
} # }
```
