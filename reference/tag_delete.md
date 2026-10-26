# Delete an existing tag reference

Delete an existing tag reference

## Usage

``` r
tag_delete(object = ".", name = NULL)
```

## Arguments

- object:

  Can be either the path (default is ".") to a repository, or a
  `git_repository` object, or a `git_tag` object. or the tag name.

- name:

  If the `object` argument is a path to a repository or a
  `git_repository`, the name of the tag to delete.

## Value

`invisible(NULL)`

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

## Create two tags
tag(repo, "Tag1", "Tag message 1")
t2 <- tag(repo, "Tag2", "Tag message 2")

## List the two tags in the repository
tags(repo)

## Delete the two tags in the repository
tag_delete(repo, "Tag1")
tag_delete(t2)

## Show the empty list with tags in the repository
tags(repo)
} # }
```
