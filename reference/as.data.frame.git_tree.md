# Coerce entries in a git_tree to a `data.frame`

The entries in a tree are coerced to a `data.frame`

## Usage

``` r
# S3 method for class 'git_tree'
as.data.frame(x, ...)
```

## Arguments

- x:

  The tree `object`

- ...:

  Additional arguments. Not used.

## Value

`data.frame`

## Details

The `data.frame` have the following columns:

- filemode:

  The UNIX file attributes of a tree entry

- type:

  String representation of the tree entry type

- sha:

  The sha of a tree entry

- name:

  The filename of a tree entry

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

## Display tree
tree(last_commit(repo))

## Coerce tree to a data.frame
df <- as.data.frame(tree(last_commit(repo)))
df
} # }
```
