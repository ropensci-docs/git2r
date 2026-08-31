# Locate the path to configuration files

Potential configuration files:

- system:

  Locate the path to the system configuration file. If '/etc/gitconfig'
  doesn't exist, it will look for '%PROGRAMFILES%'.

- xdg:

  Locate the path to the global xdg compatible configuration file. The
  xdg compatible configuration file is usually located in
  '\$HOME/.config/git/config'. This method will try to guess the full
  path to that file, if the file exists.

- global:

  The user or global configuration file is usually located in
  '\$HOME/.gitconfig'. This method will try to guess the full path to
  that file, if the file exists.

- local:

  Locate the path to the repository specific configuration file, if the
  file exists.

## Usage

``` r
git_config_files(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

a `data.frame` with one row per potential configuration file where `NA`
means not found.
