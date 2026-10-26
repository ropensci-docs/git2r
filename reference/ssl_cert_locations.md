# Set the SSL certificate-authority locations

Set the SSL certificate-authority locations

## Usage

``` r
ssl_cert_locations(filename = NULL, path = NULL)
```

## Arguments

- filename:

  Location of a file containing several certificates concatenated
  together. Default NULL.

- path:

  Location of a directory holding several certificates, one per file.
  Default NULL.

## Value

invisible(NULL)

## Note

Either parameter may be 'NULL', but not both.
