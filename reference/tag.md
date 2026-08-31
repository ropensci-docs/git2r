# Create tag targeting HEAD commit in repository

Create tag targeting HEAD commit in repository

## Usage

``` r
tag(
  object = ".",
  name = NULL,
  message = NULL,
  session = FALSE,
  tagger = NULL,
  force = FALSE
)
```

## Arguments

- object:

  The repository `object`.

- name:

  Name for the tag.

- message:

  The tag message. Specify a tag message to create an annotated tag. A
  lightweight tag is created if the message parameter is `NULL`.

- session:

  Add sessionInfo to tag message. Default is FALSE.

- tagger:

  The tagger (author) of the tag

- force:

  Overwrite existing tag. Default = FALSE

## Value

invisible(`git_tag`) object

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Commit a text file
filename <- file.path(path, "example.txt")
writeLines("Hello world!", filename)
add(repo, "example.txt")
commit(repo, "First commit message")

## Create an annotated tag
tag(repo, "v1.0", "Tag message")

## List tags
tags(repo)

## Make a change to the text file and commit.
writeLines(c("Hello world!", "HELLO WORLD!"), filename)
add(repo, "example.txt")
commit(repo, "Second commit message")

## Create a lightweight tag
tag(repo, "v2.0")

## List tags
tags(repo)
} # }
```
