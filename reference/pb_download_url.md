# Get the download url of a given file

Returns the URL download for a given file. This can be useful when using
functions that are able to accept URLs.

## Usage

``` r
pb_download_url(
  file = NULL,
  repo = guess_repo(),
  tag = "latest",
  url_type = c("browser", "api"),
  .token = gh::gh_token()
)
```

## Arguments

- file:

  character: vector of names of files to be downloaded. If `NULL`, all
  assets attached to the release will be downloaded.

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repository

- tag:

  string: tag for the GH release, defaults to "latest"

- url_type:

  choice: one of "browser" or "api" - default "browser" is a web-facing
  URL that is not subject to API ratelimits but does not work for
  private repositories. "api" URLs work for private repos, but require a
  GitHub token passed in an Authorization header (see examples)

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

## Value

the URL to download a file

## Examples

``` r
# \donttest{
#> ⠙ 6 items, page 1 | 2ms
#> [1] "https://github.com/tanho63/piggyback-tests/releases/download/v0.0.2/mtcars.csv"    
#> [2] "https://github.com/tanho63/piggyback-tests/releases/download/v0.0.2/mtcars.parquet"
#> [3] "https://github.com/tanho63/piggyback-tests/releases/download/v0.0.2/mtcars.rds"    
#> [1] "https://github.com/tanho63/piggyback-tests/releases/download/v0.0.2/mtcars.csv"
#> No encoding supplied: defaulting to UTF-8.
# }
```
