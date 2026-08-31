# Last commit

Get last commit in the current branch.

## Usage

``` r
last_commit(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Get last commit
last_commit(repo)
last_commit(path)

## Coerce the last commit to a data.frame
as.data.frame(last_commit(path), "data.frame")

## Summary of last commit in repository
summary(last_commit(repo))
} # }
```
