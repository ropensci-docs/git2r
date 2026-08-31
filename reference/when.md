# When

Help method to extract the time as a character string from a git_commit,
git_signature, git_tag and git_time object.

## Usage

``` r
when(object, tz = "GMT", origin = "1970-01-01", usetz = TRUE)
```

## Arguments

- object:

  the `object` to extract the time slot from.

- tz:

  a character string. The time zone specification to be used for the
  conversion, *if one is required*. System-specific (see [time
  zones](https://rdrr.io/r/base/timezones.html)), but `""` is the
  current time zone, and `"GMT"` is UTC (Universal Time, Coordinated).
  Invalid values are most commonly treated as UTC, on some platforms
  with a warning.

- origin:

  a date-time object, or something which can be coerced by
  `as.POSIXct(tz = "GMT")` to such an object. Optional since R 4.3.0,
  where the equivalent of `"1970-01-01"` is used.

- usetz:

  logical. Should the time zone abbreviation be appended to the output?
  This is used in printing times, and more reliable than using `"%Z"`.

## Value

A `character` vector of length one.

## See also

[`git_time`](https://docs.ropensci.org/git2r/reference/git_time.md)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a first user and commit a file
config(repo, user.name = "Alice", user.email = "alice@example.org")
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "First commit message")

## Create tag
tag(repo, "Tagname", "Tag message")

when(commits(repo)[[1]])
when(tags(repo)[[1]])
when(tags(repo)[[1]], tz = Sys.timezone())
} # }
```
