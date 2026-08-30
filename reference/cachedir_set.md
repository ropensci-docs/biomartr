# Set directory to store back end files like kingdom summaries etc

Set directory to store back end files like kingdom summaries etc

## Usage

``` r
cachedir_set(path)
```

## Arguments

- path:

  the path to cache dir, example "~/Bio_data/biomartr_cache/"

## Value

invisible(NULL), only save the file to path location

## See also

Other cachedir:
[`cachedir()`](https://docs.ropensci.org/biomartr/reference/cachedir.md)

## Examples

``` r
# By default it is tempdir()
cachedir()
#> [1] "/tmp/RtmpHL0Gk4"
# cachedir_set("~/Bio_data/biomartr_cache/")
cachedir()
#> [1] "/tmp/RtmpHL0Gk4"
```
