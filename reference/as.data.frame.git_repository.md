# Coerce Git repository to a `data.frame`

The commits in the repository are coerced to a `data.frame`

## Usage

``` r
# S3 method for class 'git_repository'
as.data.frame(x, ...)
```

## Arguments

- x:

  The repository `object`

- ...:

  Additional arguments. Not used.

## Value

`data.frame`

## Details

The `data.frame` have the following columns:

- sha:

  The 40 character hexadecimal string of the SHA-1

- summary:

  the short "summary" of the git commit message.

- message:

  the full message of a commit

- author:

  full name of the author

- email:

  email of the author

- when:

  time when the commit happened

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create three files and commit
writeLines("First file",  file.path(path, "example-1.txt"))
writeLines("Second file", file.path(path, "example-2.txt"))
writeLines("Third file",  file.path(path, "example-3.txt"))
add(repo, "example-1.txt")
commit(repo, "Commit first file")
add(repo, "example-2.txt")
commit(repo, "Commit second file")
add(repo, "example-3.txt")
commit(repo, "Commit third file")

## Coerce commits to a data.frame
df <- as.data.frame(repo)
df
} # }
```
