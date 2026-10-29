# Delete release from GitHub repo

Delete release from GitHub repo

## Usage

``` r
pb_release_delete(repo = guess_repo(), tag, .token = gh::gh_token())
```

## Arguments

- repo:

  Repository name in format "owner/repo". Defaults to `guess_repo()`.

- tag:

  tag name to delete. Must be one of those found in
  `pb_releases()$tag_name`.

- .token:

  GitHub authentication token, see `[gh::gh_token()]`

## See also

Other release_management:
[`pb_release_create()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pb_release_delete("cboettig/piggyback-tests", "v0.0.5")
} # }
```
