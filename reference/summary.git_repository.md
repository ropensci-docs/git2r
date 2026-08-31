# Summary of repository

Summary of repository

## Usage

``` r
# S3 method for class 'git_repository'
summary(object, ...)
```

## Arguments

- object:

  The repository `object`

- ...:

  Additional arguments affecting the summary produced.

## Value

None (invisible 'NULL').

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file
writeLines("Hello world!", file.path(path, "test.txt"))
summary(repo)

## Add file
add(repo, "test.txt")
summary(repo)

## Commit
commit(repo, "First commit message")
summary(repo)

## Change the file
writeLines(c("Hello again!", "Here is a second line", "And a third"),
           file.path(path, "test.txt"))
summary(repo)

## Add file and commit
add(repo, "test.txt")
commit(repo, "Second commit message")
summary(repo)
} # }
```
