# Stash

Stash

## Usage

``` r
stash(
  repo = ".",
  message = as.character(Sys.time()),
  index = FALSE,
  untracked = FALSE,
  ignored = FALSE,
  stasher = NULL
)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- message:

  Optional description. Defaults to current time.

- index:

  All changes already added to the index are left intact in the working
  directory. Default is FALSE

- untracked:

  All untracked files are also stashed and then cleaned up from the
  working directory. Default is FALSE

- ignored:

  All ignored files are also stashed and then cleaned up from the
  working directory. Default is FALSE

- stasher:

  Signature with stasher and time of stash

## Value

invisible `git_stash` object if anything to stash else NULL

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
writeLines("Hello world!", file.path(path, "test.txt"))
add(repo, 'test.txt')
commit(repo, "Commit message")

# Change file
writeLines(c("Hello world!", "HELLO WORLD!"), file.path(path, "test.txt"))

# Check status of repository
status(repo)

# Create stash in repository
stash(repo)

# Check status of repository
status(repo)

# View stash
stash_list(repo)
} # }
```
