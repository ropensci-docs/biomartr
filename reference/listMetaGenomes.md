# List available metagenomes on NCBI Genbank

List available metagenomes on NCBI genbank. NCBI genbank allows users to
download entire metagenomes of several metagenome projects. This
function lists all available metagenomes that can then be downloaded via
[`getMetaGenomes`](https://docs.ropensci.org/biomartr/reference/getMetaGenomes.md).

## Usage

``` r
listMetaGenomes(details = FALSE)
```

## Arguments

- details:

  a boolean value specifying whether only the scientific names of stored
  metagenomes shall be returned (`details = FALSE`) or all information
  such as "organism_name","bioproject", etc (`details = TRUE`).

## See also

[`getMetaGenomes`](https://docs.ropensci.org/biomartr/reference/getMetaGenomes.md),
[`getMetaGenomeSummary`](https://docs.ropensci.org/biomartr/reference/getMetaGenomeSummary.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# retrieve available metagenome projects at NCBI Genbank
listMetaGenomes()
# retrieve detailed information on available metagenome projects 
# at NCBI Genbank
listMetaGenomes(details = TRUE)
} # }
```
