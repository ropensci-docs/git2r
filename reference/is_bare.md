# Check if repository is bare

Check if repository is bare

## Usage

``` r
is_bare(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

`TRUE` if bare repository, else `FALSE`

## See also

[init](https://docs.ropensci.org/git2r/reference/init.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)
is_bare(repo)

## Initialize a bare repository
path_bare <- tempfile(pattern="git2r-")
dir.create(path_bare)
repo_bare <- init(path_bare, bare = TRUE)
is_bare(repo_bare)
} # }
```
