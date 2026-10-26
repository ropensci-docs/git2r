# Check if branch is head

Check if branch is head

## Usage

``` r
is_head(branch = NULL)
```

## Arguments

- branch:

  The branch `object` to check if it's head.

## Value

`TRUE` if branch is head, else `FALSE`.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## List branches
branches(repo)

## Check that 'master' is_head
master <- branches(repo)[[1]]
is_head(master)

## Create and checkout 'dev' branch
checkout(repo, "dev", create = TRUE)

## List branches
branches(repo)

## Check that 'master' is no longer head
is_head(master)
} # }
```
