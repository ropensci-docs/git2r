# Delete a branch

Delete a branch

## Usage

``` r
branch_delete(branch = NULL)
```

## Arguments

- branch:

  The branch

## Value

invisible NULL

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
commit_1 <- commit(repo, "First commit message")

## Create a 'dev' branch
dev <- branch_create(commit_1, name = "dev")
branches(repo)

## Delete 'dev' branch
branch_delete(dev)
branches(repo)
} # }
```
