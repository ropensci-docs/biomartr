# Main BioMart Query Function

This function takes a set of gene ids and the biomart specifications and
performs a biomart query for the given set of gene ids.

## Usage

``` r
biomart(genes, mart, dataset, attributes, filters, mute_citation = FALSE, ...)
```

## Arguments

- genes:

  a character vector storing the gene ids of a organisms of interest to
  be queried against BioMart.

- mart:

  a character string specifying the mart to be used. Users can obtain
  available marts using
  [`getMarts`](https://docs.ropensci.org/biomartr/reference/getMarts.md).

- dataset:

  a character string specifying the dataset within the mart to be used,
  e.g. `dataset` = `"hsapiens_gene_ensembl"`.

- attributes:

  a character vector specifying the attributes that shall be used, e.g.
  `attributes` = `c("start_position","end_position","description")`.

- filters:

  a character vector specifying the filter (query key) for the BioMart
  query, e.g. `filter` = `"ensembl_gene_id"`.

- mute_citation:

  logical value indicating whether citation message should be muted.

- ...:

  additional parameters for the
  [`getBM`](https://huber-group-embl.github.io/biomaRt/reference/getBM.html)
  function.

## Value

A data.table storing the initial query gene vector in the first column,
the output gene vector in the second column, and all attributes in the
following columns.

## Details

This function is the main query function of the biomartr package.

It enables to fastly access annotations of a given gene set based on the
biomaRt package implemented by Steffen Durinck et al.

## See also

Other biomaRt:
[`getAttributes()`](https://docs.ropensci.org/biomartr/reference/getAttributes.md),
[`getDatasets()`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`getMarts()`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`organismBM()`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`organismFilters()`](https://docs.ropensci.org/biomartr/reference/organismFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# 1) select a mart
getMarts()

# we will select mart 'plants_mart' and search for available datasets
getDatasets(mart = "plants_mart")

# we choose dataset 'athaliana_eg_gene' and run biomart()
# using mart: 'plants_mart', dataset: "athaliana_eg_gene"
# attributes: c("start_position","end_position","description")
# for an example gene set of Arabidopsis thaliana:
# c("AT1G06090", "AT1G06100", "AT1G06110", "AT1G06120",
#    "AT1G06130", "AT1G06200")

biomart(genes      = c("AT1G06090", "AT1G06100",
                       "AT1G06110", "AT1G06120",
                       "AT1G06130", "AT1G06200"),
        mart       = "plants_mart",
        dataset    = "athaliana_eg_gene",
        attributes = c("start_position","end_position","description"),
        filters    = "ensembl_gene_id")
} # }
```
