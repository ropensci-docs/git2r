# Create blob from file on disk

Read a file from the filesystem and write its content to the Object
Database as a loose blob. The method is vectorized and accepts a vector
of files to create blobs from.

## Usage

``` r
blob_create(repo = ".", path = NULL, relative = TRUE)
```

## Arguments

- repo:

  The repository where the blob(s) will be written. Can be a bare
  repository. A `git_repository` object, or a path to a repository, or
  `NULL`. If the `repo` argument is `NULL`, the repository is searched
  for with
  [`discover_repository`](https://docs.ropensci.org/git2r/reference/discover_repository.md)
  in the current working directory.

- path:

  The file(s) from which the blob will be created.

- relative:

  TRUE if the file(s) from which the blob will be created is relative to
  the repository's working dir. Default is TRUE.

## Value

list of S3 class git_blob `objects`

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create blobs from files relative to workdir
writeLines("Hello, world!", file.path(path, "example-1.txt"))
writeLines("test content", file.path(path, "example-2.txt"))
blob_list_1 <- blob_create(repo, c("example-1.txt",
                                   "example-2.txt"))

## Create blobs from files not relative to workdir
temp_file_1 <- tempfile()
temp_file_2 <- tempfile()
writeLines("Hello, world!", temp_file_1)
writeLines("test content", temp_file_2)
blob_list_2 <- blob_create(repo, c(temp_file_1, temp_file_2),
                           relative = FALSE)
} # }
```
