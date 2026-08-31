# Get target (sha) pointed to by a branch

Get target (sha) pointed to by a branch

## Usage

``` r
branch_target(branch = NULL)
```

## Arguments

- branch:

  The branch

## Value

sha or NA if not a direct reference

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Get target (sha) pointed to by 'master' branch
branch_target(repository_head(repo))
} # }
```
