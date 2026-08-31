# Get blame for file

Get blame for file

## Usage

``` r
blame(repo = ".", path = NULL)
```

## Arguments

- repo:

  a path to a repository or a `git_repository` object. Default is '.'

- path:

  Path to the file to consider

## Value

git_blame object with the following entries:

- path:

  The path to the file of the blame

- hunks:

  List of blame hunks

- repo:

  The git_repository that contains the file

&nbsp;

- lines_in_hunk:

  The number of lines in this hunk

- final_commit_id:

  The sha of the commit where this line was last changed

- final_start_line_number:

  The 1-based line number where this hunk begins, in the final version
  of the file

- final_signature:

  Final committer

- orig_commit_id:

  The sha of the commit where this hunk was found. This will usually be
  the same as 'final_commit_id'.

- orig_start_line_number:

  The 1-based line number where this hunk begins in the file named by
  'orig_path' in the commit specified by 'orig_commit_id'.

- orig_signature:

  Origin committer

- orig_path:

  The path to the file where this hunk originated, as of the commit
  specified by 'orig_commit_id'

- boundary:

  TRUE iff the hunk has been tracked to a boundary commit.

- repo:

  The `git_repository` object that contains the blame hunk

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

## Create a second user and change the file
config(repo, user.name = "Bob", user.email = "bob@example.org")
writeLines(c("Hello world!", "HELLO WORLD!", "HOLA"),
           file.path(path, "example.txt"))
add(repo, "example.txt")
commit(repo, "Second commit message")

## Check blame
blame(repo, "example.txt")
} # }
```
