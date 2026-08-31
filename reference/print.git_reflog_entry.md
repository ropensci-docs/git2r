# Print a reflog entry

Print a reflog entry

## Usage

``` r
# S3 method for class 'git_reflog_entry'
print(x, ...)
```

## Arguments

- x:

  The reflog entry

- ...:

  Unused

## Value

None (invisible 'NULL').

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

## View repository HEAD reflog
reflog(repo)
} # }
```
