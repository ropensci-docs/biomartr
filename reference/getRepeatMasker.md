# Repeat Masker Retrieval

Main Repeat Masker output retrieval function for an organism of
interest. By specifying the scientific name of an organism of interest
the corresponding Repeat Masker file storing the genome of the organism
of interest can be downloaded and stored locally. Repeat Masker files
can be retrieved from several databases.

## Usage

``` r
getRepeatMasker(
  db = "refseq",
  organism,
  reference = FALSE,
  skip_bacteria = TRUE,
  release = NULL,
  gunzip = FALSE,
  path = file.path("_ncbi_downloads", "repeatmasker"),
  mute_citation = FALSE
)
```

## Arguments

- db:

  a character string specifying the database from which the genome shall
  be retrieved:

  - `db = "refseq"`

  - `db = "genbank"`

- organism:

  a character string specifying the scientific name of the organism of
  interest, e.g. `organism = "Homo sapiens"`.

- reference:

  a logical value indicating whether or not a genome shall be downloaded
  if it isn't marked in the database as either a reference genome or a
  representative genome.

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- release:

  most recent database version is used. release = 75 would for human
  would give the stable GRCh37 release in ensembl. Value must be \> 46,
  since ensembl did not structure their data if the standard format
  before that.

- gunzip:

  a logical, indicating whether or not files should be unzipped.

- path:

  a character string specifying the location (a folder) in which the
  corresponding file shall be stored. Default is `path` =
  `file.path("_ncbi_downloads","repeatmasker")`.

- mute_citation:

  logical value indicating whether citation message should be muted.

## Value

File path to downloaded Repeat Masker output file.

## Details

Internally this function loads the the overview.txt file from NCBI:

refseq: `refseq_genbank_ftp_server_url_genome_specific("refseq")`

genbank: `refseq_genbank_ftp_server_url_genome_specific("genbank")`

and creates a directory '\_ncbi_downloads/repeatmasker' to store the
files of interest as fasta file for future processing. In case the
corresponding fasta file already exists within the
'\_ncbi_downloads/repeatmasker' folder and is accessible within the
workspace, no download process will be performed.

## See also

[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getGFF`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getRNA`](https://docs.ropensci.org/biomartr/reference/getRNA.md),
[`getCollection`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`meta.retrieval`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.md),
[`read_rm`](https://docs.ropensci.org/biomartr/reference/read_rm.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{

# download the Repeat Masker output file of Homo sapiens from refseq
# and store the corresponding genome file in '_ncbi_downloads/genomes'
file_path <- getRepeatMasker( db       = "refseq",
             organism = "Homo sapiens",
             path = file.path("_ncbi_downloads","repeatmasker"))

Hsap_repeatmasker <- read_rm(file_path)

} # }
```
