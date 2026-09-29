# Helper function to retrieve the assembly_summary.txt file from NCBI

Retrieval function of the assembly_summary.txt file from NCBI.

## Usage

``` r
getSummaryFile(db, kingdom, file = assemblies_info_path(db, kingdom))
```

## Arguments

- db:

  database name. E.g. `refseq` or `genbank`.

- kingdom:

  kingdom for which assembly_summary.txt file shall be retrieved. See
  also
  [`getKingdoms`](https://docs.ropensci.org/biomartr/reference/getKingdoms.md).

- file:

  path, local path to total summary file, default is in tmp folder.

## See also

[`getKingdomAssemblySummary`](https://docs.ropensci.org/biomartr/reference/getKingdomAssemblySummary.md),
[`getMetaGenomeSummary`](https://docs.ropensci.org/biomartr/reference/getMetaGenomeSummary.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
test <- getSummaryFile("refseq","plant")
test
} # }
```
