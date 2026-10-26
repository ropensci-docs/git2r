# Check if object is a git_tag object

Check if object is a git_tag object

## Usage

``` r
is_tag(object)
```

## Arguments

- object:

  Check if object is a git_tag object

## Value

TRUE if object is a git_tag, else FALSE

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

## Create tag
tag(repo, "Tagname", "Tag message")

is_tag(tags(repo)[[1]])
is_tag(last_commit(repo))
} # }
```
