# Add file(s) to index

Add file(s) to index

## Usage

``` r
add(repo = ".", path = NULL, force = FALSE)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- path:

  Character vector with file names or shell glob patterns that will
  matched against files in the repository's working directory. Each file
  that matches will be added to the index (either updating an existing
  entry or adding a new entry).

- force:

  Add ignored files. Default is FALSE.

## Value

invisible(NULL)

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file
writeLines("a", file.path(path, "a.txt"))

## Add file to repository and view status
add(repo, "a.txt")
status(repo)

## Add file with a leading './' when the repository working
## directory is the current working directory
setwd(path)
writeLines("b", file.path(path, "b.txt"))
add(repo, "./b.txt")
status(repo)

## Add a file in a sub-folder with sub-folder as the working
## directory. Create a file in the root of the repository
## working directory that will remain untracked.
dir.create(file.path(path, "sub_dir"))
setwd("./sub_dir")
writeLines("c", file.path(path, "c.txt"))
writeLines("c", file.path(path, "sub_dir/c.txt"))
add(repo, "c.txt")
status(repo)

## Add files with glob expansion when the current working
## directory is outside the repository's working directory.
setwd(tempdir())
dir.create(file.path(path, "glob_dir"))
writeLines("d", file.path(path, "glob_dir/d.txt"))
writeLines("e", file.path(path, "glob_dir/e.txt"))
writeLines("f", file.path(path, "glob_dir/f.txt"))
writeLines("g", file.path(path, "glob_dir/g.md"))
add(repo, "glob_dir/*txt")
status(repo)

## Add file with glob expansion with a relative path when
## the current working directory is inside the repository's
## working directory.
setwd(path)
add(repo, "./glob_dir/*md")
status(repo)
} # }
```
