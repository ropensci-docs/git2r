# Parents

Get parents of a commit.

## Usage

``` r
parents(object = NULL)
```

## Arguments

- object:

  a git_commit object.

## Value

list of git_commit objects

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines("First line.",
           file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "First commit message")

## commit_1 has no parents
parents(commit_1)

## Update 'example.txt' and commit
writeLines(c("First line.", "Second line."),
           file.path(path, "example.txt"))
add(repo, "example.txt")
commit_2 <- commit(repo, "Second commit message")

## commit_2 has commit_1 as parent
parents(commit_2)
} # }
```
