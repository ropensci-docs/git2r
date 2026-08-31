# Init a repository

Init a repository

## Usage

``` r
init(path = ".", bare = FALSE, branch = NULL)
```

## Arguments

- path:

  A path to where to init a git repository

- bare:

  If TRUE, a Git repository without a working directory is created at
  the pointed path. If FALSE, provided path will be considered as the
  working directory into which the .git directory will be created.

- branch:

  Use the specified name for the initial branch in the newly created
  repository. If `branch=NULL`, fall back to the default name.

## Value

A `git_repository` object

## See also

[repository](https://docs.ropensci.org/git2r/reference/repository.md)

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
