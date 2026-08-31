# Bundle bare repo of package

Clone the package git repository as a bare repository to
`pkg/inst/pkg.git`

## Usage

``` r
bundle_r_package(repo = ".")
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

## Value

Invisible bundled `git_repository` object

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repository
path <- tempfile()
dir.create(path)
path <- file.path(path, "git2r")
repo <- clone("https://github.com/ropensci/git2r.git", path)

## Bundle bare repository in package
bundle_r_package(repo)

## Build and install bundled package
wd <- setwd(dirname(path))
system(sprintf("R CMD build %s", path))
pkg <- list.files(".", pattern = "[.]tar[.]gz$")
system(sprintf("R CMD INSTALL %s", pkg))
setwd(wd)

## Reload package
detach("package:git2r", unload = TRUE)
library(git2r)

## Summarize last five commits of bundled repo
repo <- repository(system.file("git2r.git", package = "git2r"))
invisible(lapply(commits(repo, n = 5), summary))

## Plot content of bundled repo
plot(repo)
} # }
```
