# Tree

Get the tree pointed to by a commit or stash.

## Usage

``` r
tree(object = NULL)
```

## Arguments

- object:

  the `commit` or `stash` object

## Value

A S3 class git_tree object

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a first user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

tree(last_commit(repo))
} # }
```
