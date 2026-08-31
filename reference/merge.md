# Merge a branch into HEAD

Merge a branch into HEAD

## Usage

``` r
# S3 method for class 'git_branch'
merge(x, y = NULL, commit_on_success = TRUE, merger = NULL, fail = FALSE, ...)

# S3 method for class 'git_repository'
merge(x, y = NULL, commit_on_success = TRUE, merger = NULL, fail = FALSE, ...)

# S3 method for class 'character'
merge(
  x = ".",
  y = NULL,
  commit_on_success = TRUE,
  merger = NULL,
  fail = FALSE,
  ...
)
```

## Arguments

- x:

  A path (default '.') to a repository, or a `git_repository` object, or
  a `git_branch`.

- y:

  If `x` is a `git_repository`, the name of the branch to merge into
  HEAD. Not used if `x` is a `git_branch`.

- commit_on_success:

  If there are no conflicts written to the index, the merge commit will
  be committed. Default is TRUE.

- merger:

  Who made the merge. The default (`NULL`) is to use `default_signature`
  for the repository.

- fail:

  If a conflict occurs, exit immediately instead of attempting to
  continue resolving conflicts. Default is `FALSE`.

- ...:

  Additional arguments (unused).

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
## Create a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)
config(repo, user.name="Alice", user.email = "alice@example.org")

## Create a file, add and commit
writeLines("Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
           con = file.path(path, "test.txt"))
add(repo, "test.txt")
commit_1 <- commit(repo, "Commit message 1")

## Create first branch, checkout, add file and commit
checkout(repo, "branch1", create = TRUE)
writeLines("Branch 1", file.path(path, "branch-1.txt"))
add(repo, "branch-1.txt")
commit(repo, "Commit message branch 1")

## Create second branch, checkout, add file and commit
b_2 <- branch_create(commit_1, "branch2")
checkout(b_2)
writeLines("Branch 2", file.path(path, "branch-2.txt"))
add(repo, "branch-2.txt")
commit(repo, "Commit message branch 2")

## Make a change to 'test.txt'
writeLines(c("Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do",
             "eiusmod tempor incididunt ut labore et dolore magna aliqua."),
           con = file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Second commit message branch 2")

## Checkout master
checkout(repo, "master", force = TRUE)

## Merge branch 1
merge(repo, "branch1")

## Merge branch 2
merge(repo, "branch2")

## Create third branch, checkout, change file and commit
checkout(repo, "branch3", create=TRUE)
writeLines(c("Lorem ipsum dolor amet sit, consectetur adipisicing elit, sed do",
             "eiusmod tempor incididunt ut labore et dolore magna aliqua."),
           con = file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Commit message branch 3")

## Checkout master and create a change that creates a merge conflict
checkout(repo, "master", force=TRUE)
writeLines(c("Lorem ipsum dolor sit amet, adipisicing consectetur elit, sed do",
             "eiusmod tempor incididunt ut labore et dolore magna aliqua."),
           con = file.path(path, "test.txt"))
add(repo, "test.txt")
commit(repo, "Some commit message branch 1")

## Merge branch 3
merge(repo, "branch3")

## Check status; Expect to have one unstaged unmerged conflict.
status(repo)
} # }
```
