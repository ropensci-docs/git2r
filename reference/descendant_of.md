# Descendant

Determine if a commit is the descendant of another commit

## Usage

``` r
descendant_of(commit = NULL, ancestor = NULL)
```

## Arguments

- commit:

  a git_commit object. Can also be a tag or a branch, and in that case
  the commit will be the target of the tag or branch.

- ancestor:

  a git_commit object to check if ancestor to `commit`. Can also be a
  tag or a branch, and in that case the commit will be the target of the
  tag or branch.

## Value

TRUE if `commit` is descendant of `ancestor`, else FALSE

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
commit_1 <- commit(repo, "Commit message 1")
tag_1 <- tag(repo, "Tagname1", "Tag message 1")

# Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path, "test.txt"))
add(repo, "test.txt")
commit_2 <- commit(repo, "Commit message 2")
tag_2 <- tag(repo, "Tagname2", "Tag message 2")

descendant_of(commit_1, commit_2)
descendant_of(commit_2, commit_1)
descendant_of(tag_1, tag_2)
descendant_of(tag_2, tag_1)
} # }
```
