# Get the SHA-1 of a git object

Get the 40 character hexadecimal string of the SHA-1.

## Usage

``` r
sha(object)

# S3 method for class 'git_blob'
sha(object)

# S3 method for class 'git_branch'
sha(object)

# S3 method for class 'git_commit'
sha(object)

# S3 method for class 'git_note'
sha(object)

# S3 method for class 'git_reference'
sha(object)

# S3 method for class 'git_reflog_entry'
sha(object)

# S3 method for class 'git_tag'
sha(object)

# S3 method for class 'git_tree'
sha(object)

# S3 method for class 'git_fetch_head'
sha(object)

# S3 method for class 'git_merge_result'
sha(object)
```

## Arguments

- object:

  a git object to get the SHA-1 from.

## Value

The 40 character hexadecimal string of the SHA-1.

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a directory in tempdir
path <- tempfile(pattern="git2r-")
dir.create(path)

## Initialize a repository
repo <- init(path)
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file, add and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Commit message 1")

## Get the SHA-1 of the last commit
sha(last_commit(repo))
} # }
```
