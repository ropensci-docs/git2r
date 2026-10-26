# List references in a remote repository

Displays references available in a remote repository along with the
associated commit IDs. Akin to the 'git ls-remote' command.

## Usage

``` r
remote_ls(name = NULL, repo = NULL, credentials = NULL, proxy = NULL)
```

## Arguments

- name:

  Character vector with the "remote" repository URL to query or the name
  of the remote if a `repo` argument is given.

- repo:

  an optional repository object used if remotes are specified by name.

- credentials:

  The credentials for remote repository access. Default is NULL. To use
  and query an ssh-agent for the ssh key credentials, let this parameter
  be NULL (the default).

- proxy:

  Either `NULL` (the default) to disable proxy usage, `TRUE` for
  automatic proxy detection, or a character string with a proxy URL (for
  example, `"http://proxy.example.org:3128"`).

## Value

Character vector for each reference with the associated commit IDs.

## Examples

``` r
if (FALSE) { # \dontrun{
remote_ls("https://github.com/ropensci/git2r")
} # }
```
