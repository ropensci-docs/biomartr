# Check Genome Availability

This function checks the availability of a given genome on the NBCI
servers specified as scientific name.

## Usage

``` r
is.genome.available(
  db = "refseq",
  organism,
  skip_bacteria = TRUE,
  details = FALSE
)
```

## Arguments

- db:

  a character string specifying the database from which the genome shall
  be retrieved:

  - `db = "refseq"`

  - `db = "genbank"`

  - `db = "ensembl"`

  - `db = "uniprot"`

- organism:

  there are three options to characterize an organism:

  - by `scientific name`: e.g. `organism = "Homo sapiens"`

  - by `database specific accession identifier`: e.g.
    `organism = "GCF_000001405.37"` (= NCBI RefSeq identifier for
    `Homo sapiens`)

  - by `taxonomic identifier from NCBI Taxonomy`: e.g.
    `organism = "9606"` (= taxid of `Homo sapiens`)

- skip_bacteria:

  Due to its enormous dataset size (\> 700MB as of July 2023), the
  bacterial summary file will not be loaded by default anymore. If users
  wish to gain insights for the bacterial kingdom they needs to actively
  specify `skip_bacteria = FALSE`. When `skip_bacteria = FALSE` is set
  then the bacterial summary file will be downloaded.

- details:

  a logical value specifying whether or not details on genome size,
  kingdom, etc. shall be printed to the console intead of a boolean
  value.

## Value

a logical value specifing whether or not the genome of the input
organism is available. In case `details` = `TRUE` only a character
string specifying the genome details is being returned.

## Details

Internally this function calls the
[`listGenomes`](https://docs.ropensci.org/biomartr/reference/listGenomes.md)
function to detect all available genomes and checks whether or not the
specified organism is available for download.

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# checking whether the Homo sapiens genome is stored on NCBI
is.genome.available(organism = "Homo sapiens", db = "refseq")

# and printing details
is.genome.available(organism = "Homo sapiens", db = "refseq", details = TRUE)

# checking whether the Homo sapiens genome is stored on ENSEMBL
is.genome.available(organism = "Homo sapiens", db = "ensembl")

# and printing details
is.genome.available(organism = "Homo sapiens",
                    details = TRUE,
                    db = "ensembl")
} # }
```
