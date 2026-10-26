# Status

Display state of the repository working directory and the staging area.

## Usage

``` r
status(
  repo = ".",
  staged = TRUE,
  unstaged = TRUE,
  untracked = TRUE,
  ignored = FALSE,
  all_untracked = FALSE
)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- staged:

  Include staged files. Default TRUE.

- unstaged:

  Include unstaged files. Default TRUE.

- untracked:

  Include untracked files and directories. Default TRUE.

- ignored:

  Include ignored files. Default FALSE.

- all_untracked:

  Shows individual files in untracked directories if `untracked` is
  `TRUE`.

## Value

`git_status` with repository status

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Config user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file
writeLines("Hello world!", file.path(path, "test.txt"))

## Check status; untracked file
status(repo)

## Add file
add(repo, "test.txt")

## Check status; staged file
status(repo)

## Commit
commit(repo, "First commit message")

## Check status; clean
status(repo)

## Change the file
writeLines(c("Hello again!", "Here is a second line", "And a third"),
           file.path(path, "test.txt"))

## Check status; unstaged file
status(repo)

## Add file and commit
add(repo, "test.txt")
commit(repo, "Second commit message")

## Check status; clean
status(repo)
} # }
```
