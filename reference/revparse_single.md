# Revparse

Find object specified by revision.

## Usage

``` r
revparse_single(repo = ".", revision = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- revision:

  The revision string, see
  http://git-scm.com/docs/git-rev-parse.html#\_specifying_revisions

## Value

a `git_commit` or `git_tag` or `git_tree` object

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
commit(repo, "First commit message")

# Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Second commit message")

revparse_single(repo, "HEAD^")
revparse_single(repo, "HEAD:test.txt")
} # }
```
