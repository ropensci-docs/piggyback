# Create a new release on GitHub repo

Create a new release on GitHub repo

## Usage

``` r
pb_release_create(
  repo = guess_repo(),
  tag,
  commit = NULL,
  name = tag,
  body = "Data release",
  draft = FALSE,
  prerelease = FALSE,
  .token = gh::gh_token()
)
```

## Arguments

- repo:

  Repository name in format "owner/repo". Will guess the current repo if
  not specified.

- tag:

  tag to create for this release

- commit:

  Specifies the commit-ish value that determines where the Git tag is
  created from. Can be any branch or full commit SHA (not the short
  hash). Unused if the git tag already exists. Default: the repository's
  default branch (usually `master`).

- name:

  The name of the release. Defaults to tag.

- body:

  Text describing the contents of the tag. default text is "Data
  release".

- draft:

  default `FALSE`. Set to `TRUE` to create a draft (unpublished)
  release.

- prerelease:

  default `FALSE`. Set to `TRUE` to identify the release as a
  pre-release.

- .token:

  GitHub authentication token, see `[gh::gh_token()]`

## See also

Other release_management:
[`pb_release_delete()`](https://docs.ropensci.org/piggyback/reference/pb_release_delete.md)

## Examples

``` r
if (FALSE) { # \dontrun{
pb_release_create("cboettig/piggyback-tests", "v0.0.5")
} # }
```
