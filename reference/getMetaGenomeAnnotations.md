# Retrieve annotation \*.gff files for metagenomes from NCBI Genbank

Retrieve available annotation \*.gff files for metagenomes from NCBI
Genbank. NCBI Genbank allows users to download entire metagenomes and
their annotations of several metagenome projects. This function
downloads available metagenomes that can then be downloaded via
[`getMetaGenomes`](https://docs.ropensci.org/biomartr/reference/getMetaGenomes.md).

## Usage

``` r
getMetaGenomeAnnotations(
  name,
  path = file.path("_ncbi_downloads", "metagenome", "annotations"),
  metagenomes.members = dplyr::filter(getMetaGenomeSummary(), organism_name == name &
    total_gene_count > 0)
)
```

## Arguments

- name:

  metagenome name retrieved by
  [`listMetaGenomes`](https://docs.ropensci.org/biomartr/reference/listMetaGenomes.md).

- path:

  a character string specifying the location (a folder) in which the
  corresponding metagenome annotations shall be stored. Default is
  `path` = `file.path("_ncbi_downloads","metagenome","annotations")`.

- metagenomes.members:

  a tibble with selected assemblies, default:
  dplyr::filter(getMetaGenomeSummary(), organism_name == name &
  total_gene_count \> 0)). This is different to getMetaGenome since it
  requires a gff to exist, most genbank assemblies are .gbff files only,
  which are usually not useful.

## See also

[`getMetaGenomes`](https://docs.ropensci.org/biomartr/reference/getMetaGenomes.md),
[`listMetaGenomes`](https://docs.ropensci.org/biomartr/reference/listMetaGenomes.md),
[`getGFF`](https://docs.ropensci.org/biomartr/reference/getGFF.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# Frist, retrieve a list of available metagenomes
listMetaGenomes()

# Now, retrieve the 'human gut metagenome'
getMetaGenomeAnnotations(name = "human gut metagenome")
} # }
```
