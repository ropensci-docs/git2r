# Time

The class `git_time` stores the time a Git object was created.

## Usage

``` r
# S3 method for class 'git_time'
as.character(x, tz = "GMT", origin = "1970-01-01", usetz = TRUE, ...)

# S3 method for class 'git_time'
format(x, tz = "GMT", origin = "1970-01-01", usetz = TRUE, ...)

# S3 method for class 'git_time'
as.POSIXct(x, tz = "GMT", origin = "1970-01-01", ...)

# S3 method for class 'git_time'
print(x, tz = "GMT", origin = "1970-01-01", usetz = TRUE, ...)
```

## Arguments

- x:

  R object to be converted.

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

- ...:

  further arguments to be passed to or from other methods.

## Details

The default is to use `tz = "GMT"` and `origin = "1970-01-01"`. To use
your local timezone, set `tz = Sys.timezone()`.

## See also

[`when`](https://docs.ropensci.org/git2r/reference/when.md)

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

as.POSIXct(commits(repo)[[1]]$author$when)
as.POSIXct(tags(repo)[[1]]$tagger$when)
as.POSIXct(tags(repo)[[1]]$tagger$when, tz = Sys.timezone())
} # }
```
