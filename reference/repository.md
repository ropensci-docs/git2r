# Open a repository

Open a repository

## Usage

``` r
repository(path = ".", discover = TRUE)
```

## Arguments

- path:

  A path to an existing local git repository.

- discover:

  Discover repository from path. Default is TRUE.

## Value

A `git_repository` object with entries:

- path:

  Path to a git repository

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
add(repo, 'test-1.txt')
commit_1 <- commit(repo, "Commit message")

## Make one more commit
writeLines(c("Hello world!", "HELLO WORLD!"),
           file.path(path, "test-1.txt"))
add(repo, 'test-1.txt')
commit(repo, "Next commit message")

## Create one more file
writeLines("Hello world!",
           file.path(path, "test-2.txt"))

## Brief summary of repository
repo

## Summary of repository
summary(repo)

## Workdir of repository
workdir(repo)

## Check if repository is bare
is_bare(repo)

## Check if repository is empty
is_empty(repo)

## Check if repository is a shallow clone
is_shallow(repo)

## List all references in repository
references(repo)

## List all branches in repository
branches(repo)

## Get HEAD of repository
repository_head(repo)

## Check if HEAD is head
is_head(repository_head(repo))

## Check if HEAD is local
is_local(repository_head(repo))

## List all tags in repository
tags(repo)
} # }
```
