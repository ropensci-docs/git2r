# Push

Push

## Usage

``` r
push(
  object = ".",
  name = NULL,
  refspec = NULL,
  force = FALSE,
  credentials = NULL,
  set_upstream = FALSE,
  proxy = NULL
)
```

## Arguments

- object:

  path to repository, or a `git_repository` or `git_branch`.

- name:

  The remote's name. Default is NULL.

- refspec:

  The refspec to be pushed. Default is NULL.

- force:

  Force your local revision to the remote repo. Use it with care.
  Default is FALSE.

- credentials:

  The credentials for remote repository access. Default is NULL. To use
  and query an ssh-agent for the ssh key credentials, let this parameter
  be NULL (the default).

- set_upstream:

  Set the current local branch to track the remote branch. Default is
  FALSE.

- proxy:

  Either `NULL` (the default) to disable proxy usage, `TRUE` for
  automatic proxy detection, or a character string with a proxy URL (for
  example, `"http://proxy.example.org:3128"`).

## Value

invisible(NULL)

## See also

[`cred_user_pass`](https://docs.ropensci.org/git2r/reference/cred_user_pass.md),
[`cred_ssh_key`](https://docs.ropensci.org/git2r/reference/cred_ssh_key.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize two temporary repositories
path_bare <- tempfile(pattern="git2r-")
path_repo <- tempfile(pattern="git2r-")
dir.create(path_bare)
dir.create(path_repo)
repo_bare <- init(path_bare, bare = TRUE)

## Clone the bare repository. This creates remote-tracking
## branches for each branch in the cloned repository.
repo <- clone(path_bare, path_repo)

## Config user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Write to a file and commit
lines <- "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do"
writeLines(lines, file.path(path_repo, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Push commits from repository to bare repository
push(repo, "origin", "refs/heads/master")

## Now, unset the remote-tracking branch to NULL to demonstrate
## the 'set_upstream' argument. Then push with 'set_upstream = TRUE'
## to add the upstream tracking branch to branch 'master' again.
branch_get_upstream(repository_head(repo))
branch_set_upstream(repository_head(repo), NULL)
branch_get_upstream(repository_head(repo))
push(repo, "origin", "refs/heads/master", set_upstream = TRUE)
branch_get_upstream(repository_head(repo))

## Change file and commit
lines <- c(
  "Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
  "eiusmod tempor incididunt ut labore et dolore magna aliqua.")
writeLines(lines, file.path(path_repo, "example.txt"))
add(repo, "example.txt")
commit(repo, "Second commit message")

## Push commits from repository to bare repository
push(repo)

## List commits in repository and bare repository
commits(repo)
commits(repo_bare)
} # }
```
