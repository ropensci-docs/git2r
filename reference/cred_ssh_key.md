# Create a new passphrase-protected ssh key credential object

Create a new passphrase-protected ssh key credential object

## Usage

``` r
cred_ssh_key(
  publickey = ssh_path("id_rsa.pub"),
  privatekey = ssh_path("id_rsa"),
  passphrase = character(0)
)
```

## Arguments

- publickey:

  The path to the public key of the credential. Default is
  `ssh_path("id_rsa.pub")`

- privatekey:

  The path to the private key of the credential. Default is
  `ssh_path("id_rsa")`

- passphrase:

  The passphrase of the credential. Default is `character(0)`. If
  getPass is installed and private key is passphrase protected
  [`getPass::getPass()`](https://rdrr.io/pkg/getPass/man/getPass.html)
  will be called to allow for interactive and obfuscated interactive
  input of the passphrase.

## Value

A list of class `cred_ssh_key` with entries:

- publickey:

  The path to the public key of the credential

- privatekey:

  The path to the private key of the credential

- passphrase:

  The passphrase of the credential

## See also

Other git credential functions:
[`cred_env()`](https://docs.ropensci.org/git2r/reference/cred_env.md),
[`cred_token()`](https://docs.ropensci.org/git2r/reference/cred_token.md),
[`cred_user_pass()`](https://docs.ropensci.org/git2r/reference/cred_user_pass.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Create a ssh key credential object. It can optionally be
## passphrase-protected
cred <- cred_ssh_key(ssh_path("id_rsa.pub"), ssh_path("id_rsa"))
repo <- repository("git2r")
push(repo, credentials = cred)
} # }
```
