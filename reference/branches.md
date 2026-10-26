# Branches

List branches in repository

## Usage

``` r
branches(repo = ".", flags = c("all", "local", "remote"))
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- flags:

  Filtering flags for the branch listing. Valid values are 'all',
  'local' or 'remote'

## Value

list of branches in repository

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repositories
path_bare <- tempfile(pattern="git2r-")
path_repo <- tempfile(pattern="git2r-")
dir.create(path_bare)
dir.create(path_repo)
repo_bare <- init(path_bare, bare = TRUE)
repo <- clone(path_bare, path_repo)

## Config first user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path_repo, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Push commits from repository to bare repository
## Adds an upstream tracking branch to branch 'master'
push(repo, "origin", "refs/heads/master")

## List branches
branches(repo)
} # }
```
