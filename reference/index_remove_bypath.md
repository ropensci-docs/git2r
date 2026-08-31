# Remove an index entry corresponding to a file on disk

Remove an index entry corresponding to a file on disk

## Usage

``` r
index_remove_bypath(repo = ".", path = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- path:

  character vector with filenames to remove. The path must be relative
  to the repository's working folder. It may exist. If this file
  currently is the result of a merge conflict, this file will no longer
  be marked as conflicting. The data about the conflict will be moved to
  the "resolve undo" (REUC) section.

## Value

invisible(NULL)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file
writeLines("Hello world!", file.path(path, "file-to-remove.txt"))

## Add file to repository
add(repo, "file-to-remove.txt")

## View status of repository
status(repo)

## Remove file
index_remove_bypath(repo, "file-to-remove.txt")

## View status of repository
status(repo)
} # }
```
