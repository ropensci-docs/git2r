# Commit

Commit

## Usage

``` r
commit(
  repo = ".",
  message = NULL,
  all = FALSE,
  session = FALSE,
  author = NULL,
  committer = NULL
)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- message:

  The commit message.

- all:

  Stage modified and deleted files. Files not added to Git are not
  affected.

- session:

  Add sessionInfo to commit message. Default is FALSE.

- author:

  Signature with author and author time of commit.

- committer:

  Signature with committer and commit time of commit.

## Value

A list of class `git_commit` with entries:

- sha:

  The 40 character hexadecimal string of the SHA-1

- author:

  An author signature

- committer:

  The committer signature

- summary:

  The short "summary" of a git commit message, comprising the first
  paragraph of the message with whitespace trimmed and squashed.

- message:

  The message of a commit

- repo:

  The `git_repository` object that contains the commit

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")
} # }
```
