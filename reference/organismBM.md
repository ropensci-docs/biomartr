# Retrieve Ensembl Biomart marts and datasets for a query organism

This function returns either all available biomart connections for all
available organisms for which biomart access is possible, or (when
specified) returns all organism specific biomart connections.

## Usage

``` r
organismBM(organism = NULL, update = FALSE, mute_citation = TRUE)
```

## Arguments

- organism:

  a character string specifying the scientific name of a query organism.
  Default is `organism` = `NULL`. In this case all available biomart
  connections are returned.

- update:

  a logical value specifying whether or not the local listMart.txt and
  listDatasets.txt files shall be updated by remote access to BioMart.

- mute_citation:

  logical value indicating whether citation message should be muted.

## Details

This function collects all available biomart connections and returns a
table storing the organism for which biomart connections are available
as well as the corresponding mart and database.

## Note

When you run this function for the first time, the data retrieval
procedure will take some time, due to the remote access to BioMart. The
corresponding result is then saved in a \*.txt file named
"\_biomart/listDatasets.txt" in the
[`tempdir`](https://rdrr.io/r/base/tempfile.html) directory, allowing
subsequent queries to perform much faster.

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
[`organismFilters()`](https://docs.ropensci.org/biomartr/reference/organismFilters.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# returning all available biomart connections
head(organismBM(), 20)
# retrieving all available datasets and biomart connections for
# a specific query organism (scientific name)
organismBM(organism = "Homo sapiens")
# you can also update the downloaded version using
# the "update = TRUE" argument
head(organismBM(update = TRUE), 20)
} # }
```
