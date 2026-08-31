# Lookup the commit related to a git object

Lookup the commit related to a git_reference, git_tag or git_branch
object.

## Usage

``` r
lookup_commit(object)

# S3 method for class 'git_branch'
lookup_commit(object)

# S3 method for class 'git_commit'
lookup_commit(object)

# S3 method for class 'git_tag'
lookup_commit(object)

# S3 method for class 'git_reference'
lookup_commit(object)
```

## Arguments

- object:

  a git object to get the related commit from.

## Value

A git commit object.

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
writeLines(lines, con = file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Commit message 1")

## Get the commit pointed to by the 'master' branch
lookup_commit(repository_head(repo))

## Create a tag
a_tag <- tag(repo, "Tagname", "Tag message")

## Get the commit pointed to by 'a_tag'
lookup_commit(a_tag)
} # }
```
