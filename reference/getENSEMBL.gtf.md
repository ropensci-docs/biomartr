# Helper function for retrieving gtf files from ENSEMBL

This function downloads gff files of query organisms from ENSEMBL.

## Usage

``` r
getENSEMBL.gtf(organism, type = "dna", path, release = NULL)
```

## Arguments

- organism:

  Organism selector id, there are three options to characterize an
  organism:

  - by `scientific name`: e.g. `organism = "Homo sapiens"`

  - by `database specific accession identifier`: e.g.
    `organism = "GCF_000001405.37"` (= NCBI RefSeq identifier for
    `Homo sapiens`)

  - by `taxonomic identifier from NCBI Taxonomy`: e.g.
    `organism = "9606"` (= taxid of `Homo sapiens`)

- type:

  character, biological sequence type (e.g. "dna", "cds")

- path:

  location where file shall be stored.

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

## Value

character filepath to download file, returns FALSE if failed.

## Author

Hajk-Georg Drost
