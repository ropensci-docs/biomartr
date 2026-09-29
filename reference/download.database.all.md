# Download all elements of an NCBI databse

The
[`download.database`](https://docs.ropensci.org/biomartr/reference/download.database.md)
functions allows users to retrieve individual packages of a NCBI
database. This function is designed to retrieve the entire database
selected by the users (hence all packages corresponding to this
database).

## Usage

``` r
download.database.all(db, path = NULL)
```

## Arguments

- db:

  a character string specifying the database that shall be downloaded
  (selected from
  [`listDatabases`](https://docs.ropensci.org/biomartr/reference/listDatabases.md)).

- path:

  a character string specifying the location (a folder) in which the
  corresponding database shall be stored. In case this folder does not
  exist yet, it will be created.

## Value

A character vector storing the file paths of the downloaded databases.

## See also

[`download.database`](https://docs.ropensci.org/biomartr/reference/download.database.md),
[`listNCBIDatabases`](https://docs.ropensci.org/biomartr/reference/listDatabases.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# search for available NCBI databases
  listNCBIDatabases(db = "all")
# choose database NCBI nr and download compelete database
  download.database.all(db = "nr", path = "nr")
} # }
```
