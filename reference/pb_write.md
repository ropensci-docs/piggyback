# Write one object to repo/release

A convenience wrapper around writing an object to a temporary file and
then uploading to a specified repo/release.

## Usage

``` r
pb_write(
  x,
  file,
  ...,
  repo = guess_repo(),
  tag = "latest",
  write_function = guess_write_function(file),
  .token = gh::gh_token()
)
```

## Arguments

- x:

  object: memory object to save to piggyback

- file:

  string: file name

- ...:

  additional arguments passed to `write_function`

- repo:

  string: GH repository name in format "owner/repo". Default
  `guess_repo()` tries to guess based on current working directory's git
  repo

- tag:

  string: tag for the GH release, defaults to "latest"

- write_function:

  function: used to write an R object to file, where the object is
  passed as the first argument, the filename as the second argument, and
  any additional arguments are subsequently passed in via `...`. Default
  `guess_write_function(file)` will check the file extension and try to
  find an appropriate write function if the extension is one of rds,
  csv, tsv, parquet, txt, or json, and will abort if not found.

- .token:

  GitHub authentication token, see
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

## Value

Writes file to release and returns github API response

## See also

Other pb_rw:
[`guess_read_function()`](https://docs.ropensci.org/piggyback/reference/guess_read_function.md),
[`guess_write_function()`](https://docs.ropensci.org/piggyback/reference/guess_write_function.md),
[`pb_read()`](https://docs.ropensci.org/piggyback/reference/pb_read.md)

## Examples
