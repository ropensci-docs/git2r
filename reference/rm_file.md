# Remove files from the working tree and from the index

Remove files from the working tree and from the index

## Usage

``` r
rm_file(repo = ".", path = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- path:

  character vector with filenames to remove. Only files known to Git are
  removed.

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
commit(repo, "First commit message")

## Remove file
rm_file(repo, "file-to-remove.txt")

## View status of repository
status(repo)
} # }
```
