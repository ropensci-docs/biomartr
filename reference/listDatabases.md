# Retrieve a List of Available NCBI Databases for Download

This function allows you to retrieve a list of database names and
versions that can be downloaded from correspondning servers.

Database retrieval is crucial for most biological studies and analyses.
There is a vast diversity of databases that can be accessed remotely or
that can be downloaded to your local machine. This function provides an
interface to databases that can be downloaded from NCBI servers and
lists all available databases and their database version to be able to
select an appropriate database for download with
[`download.database`](https://docs.ropensci.org/biomartr/reference/download.database.md).

## Usage

``` r
listDatabases(db = "nr", update = FALSE)

listNCBIDatabases(db = "nr", update = FALSE)
```

## Arguments

- db:

  a character string specifying the name of the database that shall be
  searched for.

- update:

  a logical value specifying whether or not the local listDatabases.txt
  file shall be updated by remote access to NCBI.

## See also

[`download.database`](https://docs.ropensci.org/biomartr/reference/download.database.md),
[`download.database.all`](https://docs.ropensci.org/biomartr/reference/download.database.all.md)

## Author

Hajk-Georg Drost

## Examples

``` r
if (FALSE) { # \dontrun{
# retrieve all versions of the NCBI 'nr' database that can be downloaded
listNCBIDatabases(db = "nr")

# analogous:
# listNCBIDatabases(db = "cdd")
# listNCBIDatabases(db = "nt")
# listNCBIDatabases(db = "gss")
# listNCBIDatabases(db = "refseq_protein")
} # }
```
