# Compose usual path to ssh keys

This function provides a consistent means across OS-types to access the
`.ssh` directory.

## Usage

``` r
ssh_path(file = "")
```

## Arguments

- file:

  basename of file for which path is requested

## Value

Full path to the file

## Details

On Windows-based systems, `path.expand("~")` returns
`"C:/Users/username/Documents"`, whereas the usual path to the `.ssh`
directory is `"C:/Users/username"`.

On other operating systems, `path.expand("~")` returns the usual path to
the `.ssh` directory.

Calling `ssh_path()` with no arguments will return the usual path to the
`.ssh` directory.

## Examples

``` r
ssh_path()
#> [1] "/github/home/.ssh/"
ssh_path("is_rsa.pub")
#> [1] "/github/home/.ssh/is_rsa.pub"
```
