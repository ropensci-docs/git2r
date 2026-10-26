# Plot commits over time

Plot commits over time

## Usage

``` r
# S3 method for class 'git_repository'
plot(
  x,
  breaks = c("month", "year", "quarter", "week", "day"),
  main = NULL,
  ...
)
```

## Arguments

- x:

  The repository to plot

- breaks:

  Default is `month`. Change to year, quarter, week or day as necessary.

- main:

  Default title for the plot is "Commits on repo:" and repository
  workdir basename. Supply a new title if you desire one.

- ...:

  Additional arguments affecting the plot

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- clone("https://github.com/ropensci/git2r.git", path)

## Plot commits
plot(repo)
} # }
```
