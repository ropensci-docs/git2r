# Get HEAD for a repository

Get HEAD for a repository

## Usage

``` r
repository_head(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

NULL if unborn branch or not found. A git_branch if not a detached head.
A git_commit if detached head

## Examples

``` r
if (FALSE) { # \dontrun{
## Create and initialize a repository in a temporary directory
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file, add and commit
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "Commit message")

## Get HEAD of repository
repository_head(repo)
} # }
```
