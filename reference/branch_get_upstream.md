# Get remote tracking branch

Get remote tracking branch, given a local branch.

## Usage

``` r
branch_get_upstream(branch = NULL)
```

## Arguments

- branch:

  The branch

## Value

`git_branch` object or NULL if no remote tracking branch.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize two temporary repositories
path_bare <- tempfile(pattern="git2r-")
path_repo <- tempfile(pattern="git2r-")
dir.create(path_bare)
dir.create(path_repo)
repo_bare <- init(path_bare, bare = TRUE)
repo <- clone(path_bare, path_repo)

## Config user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path_repo, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Push commits from repository to bare repository
## Adds an upstream tracking branch to branch 'master'
push(repo, "origin", "refs/heads/master")

## Get remote tracking branch
branch_get_upstream(repository_head(repo))
} # }
```
