# Create a new plain-text username and password credential object

Create a new plain-text username and password credential object

## Usage

``` r
cred_user_pass(username = NULL, password = NULL)
```

## Arguments

- username:

  The username of the credential

- password:

  The password of the credential. If getPass is installed and the only
  input is username,
  [`getPass::getPass()`](https://rdrr.io/pkg/getPass/man/getPass.html)
  will be called to allow for interactive and obfuscated interactive
  input of the password.

## Value

A list of class `cred_user_pass` with entries:

- username:

  The username of the credential

- password:

  The password of the credential

## See also

Other git credential functions:
[`cred_env()`](https://docs.ropensci.org/git2r/reference/cred_env.md),
[`cred_ssh_key()`](https://docs.ropensci.org/git2r/reference/cred_ssh_key.md),
[`cred_token()`](https://docs.ropensci.org/git2r/reference/cred_token.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a plain-text username and password credential object
cred_user_pass("Random Developer", "SecretPassword")
} # }
```
