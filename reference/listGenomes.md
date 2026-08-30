# List All Available Genomes either by kingdom, group, or subgroup

This function retrieves the names of all genomes available on the NCBI
ftp:// server and stores the results in a file named 'overview.txt'
inside the directory \_ncbi_downloads' that is built inside the
workspace.

## Usage

``` r
listGenomes(
  db = "refseq",
  type = "all",
  subset = NULL,
  details = FALSE,
  update = FALSE,
  skip_bacteria = FALSE
)
```

## Arguments

- db:

  a character string specifying the database for which genome
  availability shall be checked. Available options are:

  - `db = "refseq"`

  - `db = "genbank"`

  - `db = "ensembl"`

- type:

  a character string specifying a potential filter of available genomes.
  Available options are:

  - `type = "all", no subset`

  - `type = "kingdom", subset on kingdom`

  - `type = "group", subset on group`

  - `type = "subgroup", subset on subgroup`

- subset:

  a character string or character vector specifying a subset of `type`.
  E.g. if users are interested in retrieving all `Eukaryota` species,
  they can specify: `type = "kingdom"` and `subset = "Eukaryota"`.

- details:

  a boolean value specifying whether only the scientific names of stored
  genomes shall be returned (details = FALSE) or all information such as

  - `organism_name`

  - `kingdoms`

  - `group`

  - `subgroup`

  - `file_size_MB`, etc.

- update:

  logical, default FALSE. If TRUE, update cached list, if FALSE use
  existing cache (if it exists). For cache location see
  [`cachedir()`](https://docs.ropensci.org/biomartr/reference/cachedir.md)

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

## Details

Internally this function loads the the overview.txt file from NCBI and
creates a directory '\_ncbi_downloads' in the `temdir()` folder to store
the overview.txt file for future processing. In case the overview.txt
file already exists within the '\_ncbi_downloads' folder and is
accessible within the workspace, no download process will be performed
again.

## Note

Please note that the ftp:// connection relies on the NCBI or ENSEMBL
server and cannot be accurately accessed via a proxy.

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# print details for refseq
listGenomes(db = "refseq")
# print details for all plants in refseq
listGenomes(db = "refseq", type = "kingdom")
# print details for all plant groups in refseq
listGenomes(db = "refseq", type = "group")
# print details for all plant subgroups in refseq
listGenomes(db = "refseq", type = "subgroup")
# Ensembl
listGenomes(db = "ensembl", type = "kingdom", subset = "EnsemblVertebrates")
} # }
```
