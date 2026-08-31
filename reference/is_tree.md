# Check if object is S3 class git_tree

Check if object is S3 class git_tree

## Usage

``` r
is_tree(object)
```

## Arguments

- object:

  Check if object is S3 class git_tree

## Value

TRUE if object is S3 class git_tree, else FALSE

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Commit a text file
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "First commit message")
tree_1 <- tree(commit_1)

## Check if tree
is_tree(commit_1)
is_tree(tree_1)
} # }
```
