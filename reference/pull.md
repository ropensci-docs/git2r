# Pull

Pull

## Usage

``` r
pull(repo = ".", credentials = NULL, merger = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- credentials:

  The credentials for remote repository access. Default is NULL. To use
  and query an ssh-agent for the ssh key credentials, let this parameter
  be NULL (the default).

- merger:

  Who made the merge, if the merge is non-fast forward merge that
  creates a merge commit. The `default_signature` for `repo` is used if
  this parameter is `NULL`.

## Value

A list of class `git_merge_result` with entries:

- up_to_date:

  TRUE if the merge is already up-to-date, else FALSE.

- fast_forward:

  TRUE if a fast-forward merge, else FALSE.

- conflicts:

  TRUE if the index contain entries representing file conflicts, else
  FALSE.

- sha:

  If the merge created a merge commit, the sha of the merge commit. NA
  if no merge commit created.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repositories
path_bare <- tempfile(pattern="git2r-")
path_repo_1 <- tempfile(pattern="git2r-")
path_repo_2 <- tempfile(pattern="git2r-")
dir.create(path_bare)
dir.create(path_repo_1)
dir.create(path_repo_2)
repo_bare <- init(path_bare, bare = TRUE)
repo_1 <- clone(path_bare, path_repo_1)

## Config first user and commit a file
config(repo_1, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path_repo_1, "example.txt"))
add(repo_1, "example.txt")
commit(repo_1, "First commit message")

## Push commits from first repository to bare repository
## Adds an upstream tracking branch to branch 'master'
push(repo_1, "origin", "refs/heads/master")

## Clone to second repository
repo_2 <- clone(path_bare, path_repo_2)
config(repo_2, user.name = "Bob", user.email = "bob@example.org")

## Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path_repo_1, "example.txt"))
add(repo_1, "example.txt")
commit(repo_1, "Second commit message")

## Push commits from first repository to bare repository
push(repo_1)

## Pull changes to repo_2
pull(repo_2)

## Change file again and commit. This time in repository 2
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad",
  "minim veniam, quis nostrud exercitation ullamco laboris nisi ut")
writeLines(lines, file.path(path_repo_2, "example.txt"))
add(repo_2, "example.txt")
commit(repo_2, "Third commit message")

## Push commits from second repository to bare repository
push(repo_2)

## Pull changes to repo_1
pull(repo_1)

## List commits in repositories
commits(repo_1)
commits(repo_2)
commits(repo_bare)
} # }
```
