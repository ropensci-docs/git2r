# Get HEAD for a repository

Get HEAD for a repository

## Usage

``` r
# S3 method for class 'git_repository'
head(x, ...)
```

## Arguments

- x:

  The repository `x` to check head

- ...:

  Additional arguments. Unused.

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
