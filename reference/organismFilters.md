# Retrieve Ensembl Biomart filters for a query organism

In addition to the
[`organismBM`](https://docs.ropensci.org/biomartr/reference/organismBM.md)
and
[`organismAttributes`](https://docs.ropensci.org/biomartr/reference/organismAttributes.md)
functions, this function returns all available filters that can be
accessed through different marts and datasets for a given query
organism.

## Usage

``` r
organismFilters(organism, update = FALSE, topic = NULL)
```

## Arguments

- organism:

  a character string specifying the scientific name of a query organism.

- update:

  a logical value specifying whether or not the local listMart.txt,
  listDatasets.txt, and listFilters_organism.txt files shall be updated
  by remote access to BioMart.

- topic:

  a character string specifying a topic (category) of filters, e.g.
  `topic` = `"id"`.

## Value

a data.frame storing corresponding filter names, description, datasets,
and marts.

## Details

For a given query organism, this function retrieves all available
filters that can be accessed through different marts and datasets.

Sometimes the same filter names correspond to different datasets and
marts causing problems when using
[`getMarts`](https://docs.ropensci.org/biomartr/reference/getMarts.md).
The approach introduced by this function provides (again) a organism
centric way of accessing organism specific filters.

The `topic` argument allows the user to search for specific filters
topics/categories for faster selection.

## Note

When you run this function for the first time, the data retrieval
procedure will take some time, due to the remote access to BioMart. The
corresponding result is then saved in a \*.txt file within the
[`tempdir`](https://rdrr.io/r/base/tempfile.html) directory named
"\_biomart/listMarts.txt","\_biomart/listDatasets.txt", and
"\_biomart/listFilters_organism.txt", allowing subsequent queries to
perform much faster.

## References

<https://biomart.org/>

Mapping identifiers for the integration of genomic datasets with the
R/Bioconductor package biomaRt. Steffen Durinck, Paul T. Spellman, Ewan
Birney and Wolfgang Huber, Nature Protocols 4, 1184-1191 (2009).

BioMart and Bioconductor: a powerful link between biological databases
and microarray data analysis. Steffen Durinck, Yves Moreau, Arek
Kasprzyk, Sean Davis, Bart De Moor, Alvis Brazma and Wolfgang Huber,
Bioinformatics 21, 3439-3440 (2005).

## See also

Other biomaRt:
[`biomart()`](https://docs.ropensci.org/biomartr/reference/biomart.md),
[`getAttributes()`](https://docs.ropensci.org/biomartr/reference/getAttributes.md),
[`getDatasets()`](https://docs.ropensci.org/biomartr/reference/getDatasets.md),
[`getMarts()`](https://docs.ropensci.org/biomartr/reference/getMarts.md),
[`organismBM()`](https://docs.ropensci.org/biomartr/reference/organismBM.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# search for filter topic "id"
head(organismFilters("Homo sapiens", topic = "id"), 20)
} # }
```
