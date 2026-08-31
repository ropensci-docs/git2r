# Default notes reference

Get the default notes reference for a repository

## Usage

``` r
note_default_ref(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

Character vector of length one with name of default notes reference

## Examples

``` r
if (FALSE) { # \dontrun{
## Create and initialize a repository in a temporary directory
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)
config(repo, user.name = "Alice", user.email = "alice@example.org")

## View default notes reference
note_default_ref(repo)
} # }
```
