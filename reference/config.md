# Config

Config file management. To display the configuration variables, call
method `config` without the `user.name`, `user.email` or `...` options.

## Usage

``` r
config(repo = NULL, global = FALSE, user.name, user.email, ...)
```

## Arguments

- repo:

  The `repository`. Default is NULL.

- global:

  Write option(s) to global configuration file. Default is FALSE.

- user.name:

  The user name. Use NULL to delete the entry

- user.email:

  The e-mail address. Use NULL to delete the entry

- ...:

  Additional options to write or delete from the configuration.

## Value

S3 class `git_config`. When writing options, the configuration is
returned invisible.

## Details

There are two ways git2r can find the local repository when writing
local options (1) Use the `repo` argument. (2) If the `repo` argument is
`NULL` but the current working directory is inside the local repository,
then `git2r` uses that repository.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern = "git2r-")
dir.create(path)
repo <- init(path)

## Set user name and email.
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Display configuration
config(repo)

## Delete user email.
config(repo, user.email = NULL)

## Display configuration
config(repo)
} # }
```
