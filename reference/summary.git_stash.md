# Summary of a stash

Summary of a stash

## Usage

``` r
# S3 method for class 'git_stash'
summary(object, ...)
```

## Arguments

- object:

  The stash `object`

- ...:

  Additional arguments affecting the summary produced.

## Value

None (invisible 'NULL').

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

# Configure a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

# Create a file, add and commit
writeLines("Hello world!", file.path(path, "test.txt"))
add(repo, 'test.txt')
commit(repo, "Commit message")

# Change file
writeLines(c("Hello world!", "HELLO WORLD!"), file.path(path, "test.txt"))

# Create stash in repository
stash(repo, "Stash message")

# View summary of stash
summary(stash_list(repo)[[1]])
} # }
```
