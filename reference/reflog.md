# List and view reflog information

List and view reflog information

## Usage

``` r
reflog(repo = ".", refname = "HEAD")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- refname:

  The name of the reference to list. 'HEAD' by default.

## Value

S3 class `git_reflog` with git_reflog_entry objects.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "Second commit message")

## Change file again and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad",
  "minim veniam, quis nostrud exercitation ullamco laboris nisi ut")
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "Third commit message")

## View reflog
reflog(repo)
} # }
```
