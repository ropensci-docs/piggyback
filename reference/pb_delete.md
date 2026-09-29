# Delete an asset attached to a release

Delete an asset attached to a release

## Usage

``` r
pb_delete(
  file = NULL,
  repo = guess_repo(),
  tag = "latest",
  .token = gh::gh_token()
)
```

## Arguments

- file:

  file(s) to be deleted from the release. If `NULL` (default when
  argument is omitted), function will delete all attachments to the
  release. delete

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repository

- tag:

  string: tag for the GH release, defaults to "latest"

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

## Value

`TRUE` (invisibly) if a file is found and deleted. Otherwise, returns
`NULL` (invisibly) if no file matching the name was found.

## Examples

``` r
if (FALSE) { # \dontrun{
readr::write_tsv(mtcars, "mtcars.tsv.gz")
## Upload
pb_upload("mtcars.tsv.gz",
          repo = "cboettig/piggyback-tests",
          overwrite = TRUE)
pb_delete("mtcars.tsv.gz",
          repo = "cboettig/piggyback-tests",
          tag = "v0.0.1")
} # }
```
