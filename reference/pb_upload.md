# Upload data to an existing release

NOTE: you must first create a release if one does not already exists.

## Usage

``` r
pb_upload(
  file,
  repo = guess_repo(),
  tag = "latest",
  name = NULL,
  overwrite = "use_timestamps",
  use_timestamps = NULL,
  show_progress = getOption("piggyback.verbose", default = interactive()),
  .token = gh::gh_token(),
  dir = NULL
)
```

## Arguments

- file:

  string: path to file to be uploaded

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repository

- tag:

  string: tag for the GH release, defaults to "latest"

- name:

  string: name for uploaded file. If not provided will use the basename
  of `file` (i.e. filename without directory)

- overwrite:

  choice: overwrite any existing file with the same name already
  attached to the on release? Options are "use_timestamps", TRUE, or
  FALSE: default "use_timestamps" will only overwrite files where the
  release timestamp is newer than the local file.

- use_timestamps:

  DEPRECATED.

- show_progress:

  logical, show a progress bar be shown for uploading? Defaults to
  [`interactive()`](https://rdrr.io/r/base/interactive.html) - can also
  set globally with options("piggyback.verbose")

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

- dir:

  directory relative to which file names should be based, defaults to
  NULL for current working directory.

## Examples

``` r
if (FALSE) { # \dontrun{
# Needs your real token to run

readr::write_tsv(mtcars,"mtcars.tsv.xz")
pb_upload("mtcars.tsv.xz", "cboettig/piggyback-tests")
} # }
```
