# Retrieve the assembly_summary.txt file from NCBI genbank metagenomes

Retrieval function of the assembly_summary.txt file from NCBI genbank
metagenomes. This files stores all available metagenome projects on NCBI
Genbank.

## Usage

``` r
getMetaGenomeSummary(
  local_file = file.path(cachedir(), "assembly_summary_metagenomes_genbank.txt")
)
```

## Arguments

- local_file:

  where to store this backend file, default: file.path(cachedir(),
  "assembly_summary_metagenomes_genbank.txt")

## Value

a tibble table

## See also

[`getKingdomAssemblySummary`](https://docs.ropensci.org/biomartr/reference/getKingdomAssemblySummary.md),
[`getSummaryFile`](https://docs.ropensci.org/biomartr/reference/getSummaryFile.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
meta.summary <- getMetaGenomeSummary()
meta.summary
} # }
```
