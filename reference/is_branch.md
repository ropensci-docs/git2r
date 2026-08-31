# Check if object is `git_branch`

Check if object is `git_branch`

## Usage

``` r
is_branch(object)
```

## Arguments

- object:

  Check if object is of class `git_branch`

## Value

TRUE if object is class `git_branch`, else FALSE

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
commit(repo, "First commit message")

branch <- branches(repo)[[1]]

## Check if branch
is_branch(branch)
} # }
```
