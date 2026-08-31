# Clone a remote repository

Clone a remote repository

## Usage

``` r
clone(
  url,
  local_path,
  bare = FALSE,
  branch = NULL,
  checkout = TRUE,
  credentials = NULL,
  progress = TRUE,
  proxy = NULL
)
```

## Arguments

- url:

  The remote repository to clone, or a local repository path.

- local_path:

  Local directory to clone to.

- bare:

  Create a bare repository. Default is FALSE.

- branch:

  The name of the branch to checkout. Default is NULL which means to use
  the remote's default branch.

- checkout:

  Checkout HEAD after the clone is complete. Default is TRUE.

- credentials:

  The credentials for remote repository access. Default is NULL. To use
  and query an ssh-agent for the ssh key credentials, let this parameter
  be NULL (the default).

- progress:

  Show progress. Default is TRUE.

- proxy:

  Either `NULL` (the default) to disable proxy usage, `TRUE` for
  automatic proxy detection, or a character string with a proxy URL (for
  example, `"http://proxy.example.org:3128"`).

## Value

A `git_repository` object.

## See also

[repository](https://docs.ropensci.org/git2r/reference/repository.md),
[`cred_user_pass`](https://docs.ropensci.org/git2r/reference/cred_user_pass.md),
[`cred_ssh_key`](https://docs.ropensci.org/git2r/reference/cred_ssh_key.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repository
path_repo_1 <- tempfile(pattern="git2r-")
path_repo_2 <- tempfile(pattern="git2r-")
dir.create(path_repo_1)
dir.create(path_repo_2)
repo_1 <- init(path_repo_1)

## Config user and commit a file
config(repo_1, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
writeLines(
    "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
    file.path(path_repo_1, "example.txt"))
add(repo_1, "example.txt")
commit(repo_1, "First commit message")

## Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path_repo_1, "example.txt"))
add(repo_1, "example.txt")
commit(repo_1, "Second commit message")

## Change file again and commit.
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad",
  "minim veniam, quis nostrud exercitation ullamco laboris nisi ut")
writeLines(lines, file.path(path_repo_1, "example.txt"))
add(repo_1, "example.txt")
commit(repo_1, "Third commit message")

## Clone to second repository
repo_2 <- clone(path_repo_1, path_repo_2)

## List commits in repositories
commits(repo_1)
commits(repo_2)
} # }
```
