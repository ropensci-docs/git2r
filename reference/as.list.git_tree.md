# Coerce entries in a git_tree to a list of entry objects

Coerce entries in a git_tree to a list of entry objects

## Usage

``` r
# S3 method for class 'git_tree'
as.list(x, ...)
```

## Arguments

- x:

  The tree `object`

- ...:

  Unused

## Value

list of entry objects

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
dir.create(file.path(path, "subfolder"))
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create three files and commit
writeLines("First file",  file.path(path, "example-1.txt"))
writeLines("Second file", file.path(path, "subfolder/example-2.txt"))
writeLines("Third file",  file.path(path, "example-3.txt"))
add(repo, c("example-1.txt", "subfolder/example-2.txt", "example-3.txt"))
commit(repo, "Commit message")

## Inspect size of each blob in tree
invisible(lapply(as(tree(last_commit(repo)), "list"),
  function(obj) {
    if (is_blob(obj))
      summary(obj)
    NULL
  }))
} # }
```
