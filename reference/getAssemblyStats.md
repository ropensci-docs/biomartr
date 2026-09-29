# Genome Assembly Stats Retrieval

Main genome assembly stats retrieval function for an organism of
interest. By specifying the scientific name of an organism of interest
the corresponding genome assembly stats file storing the assembly
statistics of the organism of interest can be downloaded and stored
locally. Genome assembly stats files can be retrieved from several
databases.

## Usage

``` r
getAssemblyStats(
  db = "refseq",
  organism,
  reference = FALSE,
  skip_bacteria = TRUE,
  release = NULL,
  type = "download",
  path = file.path("_ncbi_downloads", "genomeassembly_stats"),
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

- type:

  shall only the file be retrieved (default) `type = "download"` or
  should the corresponding file be downloaded and subsequently be
  imported `type = "import"`.

- path:

  a character string specifying the location (a folder) in which the
  corresponding file shall be stored. Default is `path` =
  `file.path("_ncbi_downloads","genomeassembly_stats")`.

- mute_citation:

  logical value indicating whether citation message should be muted.

## Value

File path to downloaded genome assembly stats file.

## Details

Internally this function loads the the overview.txt file from NCBI:

refseq: `refseq_genbank_ftp_server_url_genome_specific("refseq")`

genbank: `refseq_genbank_ftp_server_url_genome_specific("genbank")`

to retrieve available scientific names of organisms and creates a
directory '\_ncbi_downloads/genomeassembly_stats' to store the Genome
Assembly Stats of interest as text file for future processing. In case
the corresponding fasta file already exists within the
'\_ncbi_downloads/genomeassembly_stats' folder and is accessible within
the workspace, no download process will be performed.

An example genome assembly stats file can be found here:
ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/001/405/
GCF_000001405.36_GRCh38.p10/GCF_000001405.36_GRCh38.p10_assembly_stats.txt.

## See also

[`getGenome`](https://docs.ropensci.org/biomartr/reference/getGenome.md),
[`getProteome`](https://docs.ropensci.org/biomartr/reference/getProteome.md),
[`getCDS`](https://docs.ropensci.org/biomartr/reference/getCDS.md),
[`getGFF`](https://docs.ropensci.org/biomartr/reference/getGFF.md),
[`getRNA`](https://docs.ropensci.org/biomartr/reference/getRNA.md),
[`getCollection`](https://docs.ropensci.org/biomartr/reference/getCollection.md),
[`meta.retrieval`](https://docs.ropensci.org/biomartr/reference/meta.retrieval.md),
[`read_assemblystats`](https://docs.ropensci.org/biomartr/reference/read_assemblystats.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# download the genome assembly stats file of Saccharomyces cerevisiae
# from NCBI RefSeq
# and store the corresponding genome file in
# '_ncbi_downloads/genomeassembly_stats'
file_path <- getAssemblyStats( db = "refseq",
                 organism = "Saccharomyces cerevisiae",
                 path = file.path("_ncbi_downloads","genomeassembly_stats"))
# import the raw file as it is downloaded
Scerevisiae.stats <- read_assemblystats(file_path, type = "raw")

# download the genome assembly stats file of Saccharomyces cerevisiae
# from NCBI RefSeq
# and import overall statistics of the genome assembly
Scerevisiae.stats.import <- getAssemblyStats( db = "refseq",
                 organism = "Saccharomyces cerevisiae",
                 type = "import",
                 path = file.path("_ncbi_downloads","genomeassembly_stats"))
} # }
```
