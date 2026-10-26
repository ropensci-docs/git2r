# Punch card

Punch card

## Usage

``` r
punch_card(repo = ".", main = NULL, ...)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- main:

  Default title for the plot is "Punch card on repo:" and repository
  workdir basename. Supply a new title if you desire one.

- ...:

  Additional arguments affecting the plot

## Value

invisible NULL

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- clone("https://github.com/ropensci/git2r.git", path)

## Plot
punch_card(repo)
} # }
```
