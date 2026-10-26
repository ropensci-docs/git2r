# Blobs in the object database

List all blobs reachable from the commits in the object database. For
each commit, list blob's in the commit tree and sub-trees.

## Usage

``` r
odb_blobs(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

A data.frame with the following columns:

- sha:

  The sha of the blob

- path:

  The path to the blob from the tree and sub-trees

- name:

  The name of the blob from the tree that contains the blob

- len:

  The length of the blob

- commit:

  The sha of the commit

- author:

  The author of the commit

- when:

  The timestamp of the author signature in the commit

## Note

A blob sha can have several entries

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a directory in tempdir
path <- tempfile(pattern="git2r-")
dir.create(path)

## Initialize a repository
repo <- init(path)
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file, add and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Commit message 1")

## Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Commit message 2")

## Commit same content under different name in a sub-directory
dir.create(file.path(path, "sub-directory"))
file.copy(file.path(path, "test.txt"),
          file.path(path, "sub-directory", "copy.txt"))
add(repo, "sub-directory/copy.txt")
commit(repo, "Commit message 3")

## List blobs
odb_blobs(repo)
} # }
```
