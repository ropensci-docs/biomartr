# Coding Sequence Retrieval

Main retrieval function for coding sequences (CDS) of an organism of
interest. By specifying the scientific name of an organism of interest
the corresponding fasta-file storing the CDS information for the
organism of interest can be downloaded and stored locally. CDS files can
be retrieved from several databases.

## Usage

``` r
getCDS(
  db = "refseq",
  organism,
  reference = FALSE,
  skip_bacteria = TRUE,
  release = NULL,
  gunzip = FALSE,
  path = file.path("_ncbi_downloads", "CDS"),
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

- path:

  a character string specifying the location (a folder) in which the
  corresponding CDS file shall be stored. Default is `path` =
  `file.path("_ncbi_downloads","CDS")`.

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
[`getCollection()`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`getGFF()`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getGenome()`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome()`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getRNA()`](https://docs.ropensci.org/biomartr/reference/getRNA.md)

Other cds:
[`getCDSSet()`](https://docs.ropensci.org/biomartr/reference/getCDSSet.md),
[`read_cds()`](https://docs.ropensci.org/biomartr/reference/read_cds.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download the genome of Arabidopsis thaliana from refseq
# and store the corresponding genome CDS file in '_ncbi_downloads/CDS'
file_path <- getCDS( db       = "refseq",
             organism = "Arabidopsis thaliana",
             path     = file.path("_ncbi_downloads","CDS"))

Ath_CDS <- read_cds(file_path, format = "fasta")

} # }
```
