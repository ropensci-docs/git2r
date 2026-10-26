# Check if object is S3 class git_blob

Check if object is S3 class git_blob

## Usage

``` r
is_blob(object)
```

## Arguments

- object:

  Check if object is S3 class git_blob

## Value

TRUE if object is S3 class git_blob, else FALSE

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

## Check if blob
is_blob(commit_1)
is_blob(blob_1)
} # }
```
