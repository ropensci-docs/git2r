# Get the signature

Get the signature according to the repository's configuration

## Usage

``` r
default_signature(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

A `git_signature` object with entries:

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Get the default signature
default_signature(repo)

## Change user
config(repo, user.name = "Bob", user.email = "bob@example.org")

## Get the default signature
default_signature(repo)
} # }
```
