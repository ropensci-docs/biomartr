# Get directory to store back end files like kingdom summaries etc

Get directory to store back end files like kingdom summaries etc

## Usage

``` r
cachedir(non_temp_cache = "~/.biomartr_cache_dir.rds")
```

## Arguments

- non_temp_cache:

  "~/.biomartr_cache_dir.rds",

## Value

reads the rds file, and returns the path for local cache, if not
existing, use tempdir().

## See also

Other cachedir:
[`cachedir_set()`](https://docs.ropensci.org/biomartr/reference/cachedir_set.md)

## Examples

``` r
cachedir()
#> [1] "/tmp/RtmpHL0Gk4"
```
