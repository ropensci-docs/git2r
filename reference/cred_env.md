# Create a new environmental credential object

Environmental variables can be written to the file `.Renviron`. This
file is read by *R* during startup, see
[`Startup`](https://rdrr.io/r/base/Startup.html).

## Usage

``` r
cred_env(username = NULL, password = NULL)
```

## Arguments

- username:

  The name of the environmental variable that holds the username for the
  authentication.

- password:

  The name of the environmental variable that holds the password for the
  authentication.

## Value

A list of class `cred_env` with entries:

- username:

  The name of the environmental variable that holds the username for the
  authentication.

- password:

  The name of the environmental variable that holds the password for the
  authentication.

## See also

Other git credential functions:
[`cred_ssh_key()`](https://docs.ropensci.org/git2r/reference/cred_ssh_key.md),
[`cred_token()`](https://docs.ropensci.org/git2r/reference/cred_token.md),
[`cred_user_pass()`](https://docs.ropensci.org/git2r/reference/cred_user_pass.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Create an environmental credential object for the username and
## password.
cred <- cred_env("NAME_OF_ENV_VARIABLE_WITH_USERNAME",
                 "NAME_OF_ENV_VARIABLE_WITH_PASSWORD")
repo <- repository("git2r")
push(repo, credentials = cred)
} # }
```
