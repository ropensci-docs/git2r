# List stashes in repository

List stashes in repository

## Usage

``` r
stash_list(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

list of stashes in repository

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

# Configure a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

# Create a file, add and commit
writeLines("Hello world!", file.path(path, "test-1.txt"))
add(repo, 'test-1.txt')
commit(repo, "Commit message")

# Make one more commit
writeLines(c("Hello world!", "HELLO WORLD!"), file.path(path, "test-1.txt"))
add(repo, 'test-1.txt')
commit(repo, "Next commit message")

# Create one more file
writeLines("Hello world!", file.path(path, "test-2.txt"))

# Check that there are no stashes
stash_list(repo)

# Stash
stash(repo)

# Only untracked changes, therefore no stashes
stash_list(repo)

# Stash and include untracked changes
stash(repo, "Stash message", untracked=TRUE)

# View stash
stash_list(repo)
} # }
```
