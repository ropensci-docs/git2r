# Set the remote's url in the configuration

This assumes the common case of a single-url remote and will otherwise
raise an error.

## Usage

``` r
remote_set_url(repo = ".", name = NULL, url = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- name:

  The name of the remote

- url:

  The `url` to set

## Value

NULL, invisibly

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user and commit a file
config(repo, user.name="Alice", user.email="alice@example.org")
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Add a remote
remote_add(repo, "playground", "https://example.org/git2r/playground")
remotes(repo)
remote_url(repo, "playground")

## Rename a remote
remote_rename(repo, "playground", "foobar")
remotes(repo)
remote_url(repo, "foobar")

## Set remote url
remote_set_url(repo, "foobar", "https://example.org/git2r/foobar")
remotes(repo)
remote_url(repo, "foobar")

## Remove a remote
remote_remove(repo, "foobar")
remotes(repo)
} # }
```
