# List all assets attached to a release

List all assets attached to a release

## Usage

``` r
pb_list(repo = guess_repo(), tag = NULL, .token = gh::gh_token())
```

## Arguments

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repository

- tag:

  which release tag(s) do we want information for? If `NULL` (default),
  will return a table for all available release tags.

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

## Value

a data.frame of release asset names, release tag, timestamp, owner, and
repo.

## See also

`pb_releases` for a list of all releases in repository

## Examples

``` r
if (FALSE) { # \dontrun{
pb_list("cboettig/piggyback-tests")
} # }
```
