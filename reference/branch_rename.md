# Rename a branch

Rename a branch

## Usage

``` r
branch_rename(branch = NULL, name = NULL, force = FALSE)
```

## Arguments

- branch:

  Branch to rename

- name:

  The new name for the branch

- force:

  Overwrite existing branch. Default is FALSE

## Value

invisible renamed `git_branch` object

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Rename 'master' branch to 'dev'
branches(repo)
branch_rename(repository_head(repo), "dev")
branches(repo)
} # }
```
