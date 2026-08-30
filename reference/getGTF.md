# Genome Annotation Retrieval (GTF)

Main retrieval function for GTF files of an organism of interest. By
specifying the scientific name of an organism of interest the
corresponding GTF file storing the annotation for the organism of
interest can be downloaded and stored locally. GTF files can be
retrieved from several databases.

## Usage

``` r
getGTF(
  db = "ensembl",
  organism,
  reference = FALSE,
  remove_annotation_outliers = FALSE,
  path = file.path("ensembl", "annotation"),
  release = NULL,
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

- release:

  a numeric, the database release version of ENSEMBL (`db = "ensembl"`).
  Default is `release = NULL` meaning that the most recent database
  version is used. `release = 75` would for human would give the stable
  GRCh37 release in ensembl. Value must be \> 46, since ensembl did not
  structure their data if the standard format before that.

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
# download the annotation of Homo sapiens from ensembl
# and store the corresponding genome file in 'ensembl/annotation'
getGTF(db            = "ensembl",
       organism      = "Homo sapiens",
       path          = file.path("ensembl","annotation"))

getGTF(db            = "ensembl",
       organism      = "Homo sapiens",
       path          = file.path("ensembl","annotation"),
       assembly_type = "primary_assembly")

} # }
```
