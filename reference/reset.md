# Reset current HEAD to the specified state

Reset current HEAD to the specified state

## Usage

``` r
reset(object, reset_type = c("soft", "mixed", "hard"), path = NULL)
```

## Arguments

- object:

  Either a `git_commit`, a `git_repository` or a character vector. If
  `object` is a `git_commit`, HEAD is moved to the `git_commit`. If
  `object` is a `git_repository`, resets the index entries in the `path`
  argument to their state at HEAD. If `object` is a character vector
  with paths, resets the index entries in `object` to their state at
  HEAD if the current working directory is in a repository.

- reset_type:

  If object is a 'git_commit', the kind of reset operation to perform.
  'soft' means the HEAD will be moved to the commit. 'mixed' reset will
  trigger a 'soft' reset, plus the index will be replaced with the
  content of the commit tree. 'hard' reset will trigger a 'mixed' reset
  and the working directory will be replaced with the content of the
  index.

- path:

  If object is a 'git_repository', resets the index entries for all
  paths to their state at HEAD.

## Value

invisible NULL

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

# Configure a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file, add and commit
writeLines("Hello world!", file.path(path, "test-1.txt"))
add(repo, "test-1.txt")
commit_1 <- commit(repo, "Commit message")

## Change and stage the file
writeLines(c("Hello world!", "HELLO WORLD!"), file.path(path, "test-1.txt"))
add(repo, "test-1.txt")
status(repo)

## Unstage file
reset(repo, path = "test-1.txt")
status(repo)

## Make one more commit
add(repo, "test-1.txt")
commit(repo, "Next commit message")

## Create one more file
writeLines("Hello world!", file.path(path, "test-2.txt"))

## 'soft' reset to first commit and check status
reset(commit_1)
status(repo)

## 'mixed' reset to first commit and check status
commit(repo, "Next commit message")
reset(commit_1, "mixed")
status(repo)

## 'hard' reset to first commit and check status
add(repo, "test-1.txt")
commit(repo, "Next commit message")
reset(commit_1, "hard")
status(repo)
} # }
```
