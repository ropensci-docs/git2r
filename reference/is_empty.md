# Check if repository is empty

Check if repository is empty

## Usage

``` r
is_empty(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

`TRUE` if repository is empty else `FALSE`.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Check if it's an empty repository
is_empty(repo)

## Commit a file
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Check if it's an empty repository
is_empty(repo)
} # }
```
