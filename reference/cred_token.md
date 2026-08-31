# Create a new personal access token credential object

The personal access token is stored in an envrionmental variable.
Environmental variables can be written to the file `.Renviron`. This
file is read by *R* during startup, see
[`Startup`](https://rdrr.io/r/base/Startup.html). On GitHub, personal
access tokens function like ordinary OAuth access tokens. They can be
used instead of a password for Git over HTTPS, see the “Creating a
personal access token” article on GitHub Docs.

## Usage

``` r
cred_token(token = "GITHUB_PAT")
```

## Arguments

- token:

  The name of the environmental variable that holds the personal access
  token for the authentication. Default is `GITHUB_PAT`.

## Value

A list of class `cred_token` with entry:

- token:

  The name of the environmental variable that holds the personal access
  token for the authentication.

## See also

Other git credential functions:
[`cred_env()`](https://docs.ropensci.org/git2r/reference/cred_env.md),
[`cred_ssh_key()`](https://docs.ropensci.org/git2r/reference/cred_ssh_key.md),
[`cred_user_pass()`](https://docs.ropensci.org/git2r/reference/cred_user_pass.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a personal access token credential object.
## This example assumes that the token is stored in
## the 'GITHUB_PAT' environmental variable.
repo <- repository("git2r")
cred <- cred_token()
push(repo, credentials = cred)
} # }
```
