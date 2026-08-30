# Retrieve metagenomes from NCBI Genbank

Retrieve available metagenomes from NCBI Genbank. NCBI Genbank allows
users to download entire metagenomes of several metagenome projects.
This function downloads available metagenomes that can then be
downloaded via `getMetaGenomes`.

## Usage

``` r
getMetaGenomes(
  name,
  path = file.path("_ncbi_downloads", "metagenome"),
  metagenomes.members = dplyr::filter(getMetaGenomeSummary(), organism_name == name)
)
```

## Arguments

- name:

  metagenome name retrieved by
  [`listMetaGenomes`](https://docs.ropensci.org/biomartr/reference/listMetaGenomes.md).

- path:

  a character string specifying the location (a folder) in which the
  corresponding metagenome shall be stored. Default is `path` =
  `file.path("_ncbi_downloads","metagenome")`.

- metagenomes.members:

  a tibble of metagenome assemblies, default:
  dplyr::filter(getMetaGenomeSummary(), organism_name == name)

## See also

[`getMetaGenomeAnnotations`](https://docs.ropensci.org/biomartr/reference/getMetaGenomeAnnotations.md),
[`listMetaGenomes`](https://docs.ropensci.org/biomartr/reference/listMetaGenomes.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# Frist, retrieve a list of available metagenomes
listMetaGenomes()

# Now, retrieve the 'human gut metagenome'
getMetaGenomes(name = "human gut metagenome")
} # }
```
