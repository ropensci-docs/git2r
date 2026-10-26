# Is blob binary

Is blob binary

## Usage

``` r
is_binary(blob = NULL)
```

## Arguments

- blob:

  The blob `object`.

## Value

TRUE if binary data, FALSE if not.

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
writeLines("Hello world!", file.path(path, "example.txt"))
add(repo, "example.txt")
commit_1 <- commit(repo, "First commit message")

## Check if binary
b_text <- tree(commit_1)["example.txt"]
is_binary(b_text)

## Commit plot file (binary)
x <- 1:100
y <- x^2
png(file.path(path, "plot.png"))
plot(y ~ x, type = "l")
dev.off()
add(repo, "plot.png")
commit_2 <- commit(repo, "Second commit message")

## Check if binary
b_png <- tree(commit_2)["plot.png"]
is_binary(b_png)
} # }
```
