# Determine the sha from a blob in a file

The blob is not written to the object database.

## Usage

``` r
hashfile(path = NULL)
```

## Arguments

- path:

  The path vector with files to hash.

## Value

A vector with the sha for each file in path.

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a file. NOTE: The line endings from writeLines gives
## LF (line feed) on Unix/Linux and CRLF (carriage return, line feed)
## on Windows. The example use writeChar to have more control.
path <- tempfile()
f <- file(path, "wb")
writeChar("Hello, world!\n", f, eos = NULL)
close(f)

## Generate hash
hashfile(path)
identical(hashfile(path), hash("Hello, world!\n"))
} # }
```
