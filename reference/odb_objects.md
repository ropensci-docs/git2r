# List all objects available in the database

List all objects available in the database

## Usage

``` r
odb_objects(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

A data.frame with the following columns:

- sha:

  The sha of the object

- type:

  The type of the object

- len:

  The length of the object

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

## Create tag
tag(repo, "Tagname", "Tag message")

## List objects in repository
odb_objects(repo)
} # }
```
