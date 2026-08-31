# Remove the note for an object

Remove the note for an object

## Usage

``` r
note_remove(note = NULL, author = NULL, committer = NULL)
```

## Arguments

- note:

  The note to remove

- author:

  Signature of the notes commit author.

- committer:

  Signature of the notes commit committer.

## Value

invisible NULL

## Examples

``` r
if (FALSE) { # \dontrun{
## Create and initialize a repository in a temporary directory
path <- tempfile(pattern="git2r-")
dir.create(path)
repo <- init(path)
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create a file, add and commit
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "Commit message 1")


## Create note in default namespace
note_1 <- note_create(commit_1, "Note-1")

## Create note in named (review) namespace
note_2 <- note_create(commit_1, "Note-2", ref="refs/notes/review")

## List notes in default namespace
notes(repo)

## List notes in 'review' namespace
notes(repo, "review")

## Remove notes
note_remove(note_1)
note_remove(note_2)

## List notes in default namespace
notes(repo)

## List notes in 'review' namespace
notes(repo, "review")
} # }
```
