# Determine the sha from a blob string

The blob is not written to the object database.

## Usage

``` r
hash(data = NULL)
```

## Arguments

- data:

  The string vector to hash.

## Value

A string vector with the sha for each string in data.

## Examples

``` r
if (FALSE) { # \dontrun{
identical(hash(c("Hello, world!\n",
                 "test content\n")),
               c("af5626b4a114abcb82d63db7c8082c3c4756e51b",
                 "d670460b4b4aece5915caf5c68d12f560a9fe3e4"))
} # }
```
