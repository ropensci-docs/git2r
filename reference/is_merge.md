# Is merge

Determine if a commit is a merge commit, i.e. has more than one parent.

## Usage

``` r
is_merge(commit = NULL)
```

## Arguments

- commit:

  a git_commit object.

## Value

TRUE if commit has more than one parent, else FALSE

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines(c("First line in file 1.", "Second line in file 1."),
           file.path(path, "example-1.txt"))
add(repo, "example-1.txt")
commit(repo, "First commit message")

## Create and add one more file
writeLines(c("First line in file 2.", "Second line in file 2."),
           file.path(path, "example-2.txt"))
add(repo, "example-2.txt")
commit(repo, "Second commit message")

## Create a new branch 'fix'
checkout(repo, "fix", create = TRUE)

## Update 'example-1.txt' (swap words in first line) and commit
writeLines(c("line First in file 1.", "Second line in file 1."),
           file.path(path, "example-1.txt"))
add(repo, "example-1.txt")
commit(repo, "Third commit message")

checkout(repo, "master")

## Update 'example-2.txt' (swap words in second line) and commit
writeLines(c("First line in file 2.", "line Second in file 2."),
           file.path(path, "example-2.txt"))
add(repo, "example-2.txt")
commit(repo, "Fourth commit message")

## Merge 'fix'
merge(repo, "fix")

## Display parents of last commit
parents(lookup(repo, branch_target(repository_head(repo))))

## Check that last commit is a merge
is_merge(lookup(repo, branch_target(repository_head(repo))))
} # }
```
