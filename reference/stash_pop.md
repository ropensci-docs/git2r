# Pop stash

Apply a single stashed state from the stash list and remove it from the
list if successful.

## Usage

``` r
stash_pop(object = ".", index = 1)
```

## Arguments

- object:

  path to a repository, or a `git_repository` object, or the stash
  `object` to pop. Default is a `path = '.'` to a reposiory.

- index:

  The index to the stash to pop. Only used when `object` is a path to a
  repository or a `git_repository` object. Default is `index = 1`.

## Value

invisible NULL

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

# Create stash in repository
stash(repo)

# Change file
writeLines(c("Hello world!", "HeLlO wOrLd!"), file.path(path, "test.txt"))

# Create stash in repository
stash(repo)

# View stashes
stash_list(repo)

# Read file
readLines(file.path(path, "test.txt"))

# Pop latest git_stash object in repository
stash_pop(stash_list(repo)[[1]])

# Read file
readLines(file.path(path, "test.txt"))

# View stashes
stash_list(repo)
} # }
```
