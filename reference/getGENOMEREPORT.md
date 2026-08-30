# Retrieve NCBI GENOME_REPORTS file

Retrieves NCBI GENOME_REPORTS file from
ftp://ftp.ncbi.nlm.nih.gov/genomes/GENOME_REPORTS/overview.txt.

## Usage

``` r
getGENOMEREPORT(
  local_file = file.path(cachedir(), "_ncbi_downloads", "overview.txt")
)
```

## Arguments

- local_file:

  character, file path, default: file.path(cachedir(),
  "\_ncbi_downloads", "overview.txt")

## Value

a tibble object with the report

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
report <- getGENOMEREPORT()
report
} # }
```
