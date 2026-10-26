# Check if object is a git_commit object

Check if object is a git_commit object

## Usage

``` r
is_commit(object)
```

## Arguments

- object:

  Check if object is a git_commit object

## Value

TRUE if object is a git_commit, else FALSE

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Commit a text file
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "First commit message")

## Check if commit
is_commit(commit_1)
} # }
```
