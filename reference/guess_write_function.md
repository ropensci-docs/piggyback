# Guess write function from file extension

This function accepts a filename and tries to return a valid function
for writing to it.

## Usage

``` r
guess_write_function(file)
```

## Arguments

- file:

  filename to parse

## Value

function for reading the file, if found

## Details

`guess_write_function` understands the following file extensions:

- rds with `saveRDS`

- csv, csv.gz, csv.xz with
  [`utils::write.csv`](https://rdrr.io/r/utils/write.table.html)

- tsv, tsv.gz, tsv.xz with a modified
  [`utils::write.csv`](https://rdrr.io/r/utils/write.table.html) where
  sep is set to `"\t"`

- parquet with
  [`arrow::write_parquet`](https://arrow.apache.org/docs/r/reference/write_parquet.html)

- txt, txt.gz, txt.xz with `writeLines`

- json, json.gz, json.xz with
  [`jsonlite::write_json`](https://jeroen.r-universe.dev/jsonlite/reference/read_json.html)

## See also

Other pb_rw:
[`guess_read_function()`](https://docs.ropensci.org/piggyback/reference/guess_read_function.md),
[`pb_read()`](https://docs.ropensci.org/piggyback/reference/pb_read.md),
[`pb_write()`](https://docs.ropensci.org/piggyback/reference/pb_write.md)
