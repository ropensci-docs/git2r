# Size in bytes of the contents of a blob

Size in bytes of the contents of a blob

## Usage

``` r
# S3 method for class 'git_blob'
length(x)
```

## Arguments

- x:

  The blob `object`

## Value

a non-negative integer

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
blob_1 <- tree(commit_1)["example.txt"]

## Get length in size of bytes of the content of the blob
length(blob_1)
} # }
```
