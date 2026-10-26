# Determine if a directory is in a git repository

The lookup start from path and walk across parent directories if nothing
has been found.

## Usage

``` r
in_repository(path = ".")
```

## Arguments

- path:

  The path to the directory.

## Value

TRUE if directory is in a git repository else FALSE

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Check if path is in a git repository
in_repository(path)

## Check if working directory is in a git repository
setwd(path)
in_repository()
} # }
```
