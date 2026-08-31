# Content of blob

Content of blob

## Usage

``` r
content(blob = NULL, split = TRUE, raw = FALSE)
```

## Arguments

- blob:

  The blob object.

- split:

  Split blob content to text lines. Default TRUE.

- raw:

  When `TRUE`, get the content of the blob as a raw vector, else as a
  character vector. Default is `FALSE`.

## Value

The content of the blob. NA_character\_ if the blob is binary and `raw`
is `FALSE`.

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

## Display content of blob.
content(tree(commits(repo)[[1]])["example.txt"])
} # }
```
