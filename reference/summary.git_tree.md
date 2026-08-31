# Summary of tree

Summary of tree

## Usage

``` r
# S3 method for class 'git_tree'
summary(object, ...)
```

## Arguments

- object:

  The tree `object`

- ...:

  Additional arguments affecting the summary produced.

## Value

None (invisible 'NULL').

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

summary(tree(last_commit(repo)))
} # }
```
