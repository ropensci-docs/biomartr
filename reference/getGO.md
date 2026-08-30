# Gene Ontology Query

This function takes a gene id as character vector from a given query
organism and returns the corresponding GO terms and additional GO
information.

## Usage

``` r
getGO(organism, genes, filters, ...)
```

## Arguments

- organism:

  a character string specifying the scientific name of a query organism.

- genes:

  a character vector storing the gene ids of a organisms of interest to
  be queried against Ensembl Biomart.

- filters:

  a character vector specifying the filter (query key) for the Ensembl
  Biomart query, e.g. `filter` = `"ensembl_gene_id"`.

- ...:

  additional parameters that can be passed to the
  [`biomart`](https://docs.ropensci.org/biomartr/reference/biomart.md)
  function.

## Details

This function takes the scientific name of a query organism, a set of
genes for which GO terms and additional information shall be retrieved,
and a filter argument that specifies the attribute for the query genes.

## See also

[`biomart`](https://docs.ropensci.org/biomartr/reference/biomart.md),
[`organismFilters`](https://docs.ropensci.org/biomartr/reference/organismFilters.md),
[`organismBM`](https://docs.ropensci.org/biomartr/reference/organismBM.md),
[`getBM`](https://huber-group-embl.github.io/biomaRt/reference/getBM.html),
[`getMarts`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`getDatasets`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`getFilters`](https://docs.ropensci.org/biomartr/reference/getFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{ 
GO_tbl <- getGO(organism = "Arabidopsis thaliana", 
                genes    = c("AT1G06090", "AT1G06100"),
                filters  = "ensembl_gene_id")

# look at the result
head(GO_tbl)
} # }
```
