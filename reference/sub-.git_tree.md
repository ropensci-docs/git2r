# Extract object from tree

Lookup a tree entry by its position in the tree

## Usage

``` r
# S3 method for class 'git_tree'
x[i]
```

## Arguments

- x:

  The tree `object`

- i:

  The index (integer or logical) of the tree object to extract. If
  negative values, all elements except those indicated are selected. A
  character vector to match against the names of objects to extract.

## Value

Git object

## Examples

``` r
if (FALSE) { # \dontrun{
##' Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
dir.create(file.path(path, "subfolder"))
repo <- init(path)

##' Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

##' Create three files and commit
writeLines("First file",  file.path(path, "example-1.txt"))
writeLines("Second file", file.path(path, "subfolder/example-2.txt"))
writeLines("Third file",  file.path(path, "example-3.txt"))
add(repo, c("example-1.txt", "subfolder/example-2.txt", "example-3.txt"))
new_commit <- commit(repo, "Commit message")

##' Pick a tree in the repository
tree_object <- tree(new_commit)

##' Display tree
tree_object

##' Select item by name
tree_object["example-1.txt"]

##' Select first item in tree
tree_object[1]

##' Select first three items in tree
tree_object[1:3]

##' Select all blobs in tree
tree_object[vapply(as(tree_object, 'list'), is_blob, logical(1))]
} # }
```
