# Download sequence or annotation from ENSEMBL

Backend function for retrieving files sequence and annotation files from
the ENSEMBL ftp server

## Usage

``` r
getENSEMBL(
  organism,
  type = "dna",
  id.type = "toplevel",
  release = NULL,
  path,
  format
)
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

- id.type:

  a character, default "toplevel". id type of assembly, either
  "toplevel" or "primary_assembly" for genomes. Can be other strings,
  for non genome objects.

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

- path:

  location where file shall be stored.

- format:

  character, For annotation: default: "gff3", alternative "gtf" for
  ensembl.  
  For assembly_stats, alternatives "download" / "txt" (download only),
  "import" import dataset.

## Value

either a character path to downloaded file, or a logical FALSE,
specifying failure.

## Author

Hajk-Georg Drost
