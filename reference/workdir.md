# Workdir of repository

Workdir of repository

## Usage

``` r
workdir(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

Character vector with the path of the workdir. If the repository is
bare, `NULL` will be returned.

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a directory in tempdir
path <- tempfile(pattern="git2r-")
dir.create(path)

## Initialize a repository
repo <- init(path)

## Get the path of the workdir for repository
workdir(repo)
} # }
```
