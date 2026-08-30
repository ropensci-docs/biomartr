# Download a NCBI Database to Your Local Hard Drive

This function allows users to download a database selected by
[`listDatabases`](https://docs.ropensci.org/biomartr/reference/listDatabases.md)
to their local hard drive.

## Usage

``` r
download.database(db, path = "database")
```

## Arguments

- db:

  a character string specifying the database that shall be downloaded
  (selected from
  [`listDatabases`](https://docs.ropensci.org/biomartr/reference/listDatabases.md)).

- path:

  a character string specifying the location (a folder) in which the
  corresponding database shall be stored. Default is
  `path = "database"`. In case this folder does not exist yet, it will
  be created.

## Value

File path to the downloaded database file.

## Details

This function downloads large databases to your hard drive. For this
purpose a folder named `database` (default) is created and the
correspondning database then stored in this folder.

## See also

[`download.database.all`](https://docs.ropensci.org/biomartr/reference/download.database.all.md),
[`listDatabases`](https://docs.ropensci.org/biomartr/reference/listDatabases.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
  # search for available NCBI nr databases
  listNCBIDatabases(db = "nr")
  # select NCBI nr version 27 =  "nr.27.tar.gz"
  # and download it to your hard drive
  # -> please note that large databases take some time for download!
  download.database(db = "nr.27.tar.gz")
} # }
```
