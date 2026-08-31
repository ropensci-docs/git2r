# List the contents of a tree object

Traverse the entries in a tree and its subtrees. Akin to the 'git
ls-tree' command.

## Usage

``` r
ls_tree(tree = NULL, repo = ".", recursive = TRUE)
```

## Arguments

- tree:

  default (`NULL`) is the tree of the last commit in `repo`. Can also be
  a `git_tree` object or a character that identifies a tree in the
  repository (see ‘Examples’).

- repo:

  never used if `tree` is a `git_tree` object. A `git_repository`
  object, or a path (default = '.') to a repository.

- recursive:

  default is to recurse into sub-trees.

## Value

A data.frame with the following columns:

- mode:

  UNIX file attribute of the tree entry

- type:

  type of object

- sha:

  sha of the object

- path:

  path relative to the root tree

- name:

  filename of the tree entry

- len:

  object size of blob (file) entries. NA for other objects.

## Examples

``` r
if (FALSE) { # \dontrun{
## Initialize a temporary repository
path <- tempfile(pattern="git2r-")
dir.create(path)
dir.create(file.path(path, "subfolder"))
repo <- init(path)

## Create a user
config(repo, user.name = "Alice", user.email = "alice@example.org")

## Create three files and commit
writeLines("First file",  file.path(path, "example-1.txt"))
writeLines("Second file", file.path(path, "subfolder/example-2.txt"))
writeLines("Third file",  file.path(path, "example-3.txt"))
add(repo, c("example-1.txt", "subfolder/example-2.txt", "example-3.txt"))
commit(repo, "Commit message")

## Traverse tree entries and its subtrees.
## Various approaches that give identical result.
ls_tree(tree = tree(last_commit(path)))
ls_tree(tree = tree(last_commit(repo)))
ls_tree(repo = path)
ls_tree(repo = repo)

## Skip content in subfolder
ls_tree(repo = repo, recursive = FALSE)

## Start in subfolder
ls_tree(tree = "HEAD:subfolder", repo = repo)
} # }
```
