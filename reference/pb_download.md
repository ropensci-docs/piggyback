# Download data from an existing release

Download data from an existing release

## Usage

``` r
pb_download(
  file = NULL,
  dest = ".",
  repo = guess_repo(),
  tag = "latest",
  overwrite = TRUE,
  ignore = "manifest.json",
  use_timestamps = TRUE,
  show_progress = getOption("piggyback.verbose", default = interactive()),
  .token = gh::gh_token()
)
```

## Arguments

- file:

  character: vector of names of files to be downloaded. If `NULL`, all
  assets attached to the release will be downloaded.

- dest:

  character: path to destination directory (if length one) or vector of
  destination filepaths the same length as `file`. Any directories in
  the path provided must already exist.

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repository

- tag:

  string: tag for the GH release, defaults to "latest"

- overwrite:

  boolean: should any local files of the same name be overwritten?
  default `TRUE`

- ignore:

  character: vector of files to ignore (used if downloading "all" via
  `file=NULL`)

- use_timestamps:

  DEPRECATED.

- show_progress:

  logical, show a progress bar be shown for uploading? Defaults to
  [`interactive()`](https://rdrr.io/r/base/interactive.html) - can also
  set globally with options("piggyback.verbose")

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

## Examples

``` r
# \donttest{
#> ⠙ 4 items, page 1 | 2ms
# }
```
