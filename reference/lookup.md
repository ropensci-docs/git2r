# Lookup

Lookup one object in a repository.

## Usage

``` r
lookup(repo = ".", sha = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- sha:

  The identity of the object to lookup. Must be 4 to 40 characters long.

## Value

a `git_blob` or `git_commit` or `git_tag` or `git_tree` object

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "First commit message")

## Create tag
tag(repo, "Tagname", "Tag message")

## First, get SHAs to lookup in the repository
sha_commit <- sha(commit_1)
sha_tree <- sha(tree(commit_1))
sha_blob <- sha(tree(commit_1)["example.txt"])
sha_tag <- sha(tags(repo)[[1]])

## SHAs
sha_commit
sha_tree
sha_blob
sha_tag

## Lookup objects
lookup(repo, sha_commit)
lookup(repo, sha_tree)
lookup(repo, sha_blob)
lookup(repo, sha_tag)

## Lookup objects, using only the first seven characters
lookup(repo, substr(sha_commit, 1, 7))
lookup(repo, substr(sha_tree, 1, 7))
lookup(repo, substr(sha_blob, 1, 7))
lookup(repo, substr(sha_tag, 1, 7))
} # }
```
