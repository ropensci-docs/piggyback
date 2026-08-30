# Guess read function from file extension

This function accepts a filename and tries to return a valid function
for reading it.

## Usage

``` r
guess_read_function(file)
```

## Arguments

- file:

  filename to parse

## Value

function for reading the file, if found

## Details

`guess_read_function` understands the following file extensions:

- rds with `readRDS`

- csv, csv.gz, csv.xz with
  [`utils::read.csv`](https://rdrr.io/r/utils/read.table.html)

- tsv, tsv.gz, tsv.xz with
  [`utils::read.delim`](https://rdrr.io/r/utils/read.table.html)

- parquet with
  [`arrow::read_parquet`](https://arrow.apache.org/docs/r/reference/read_parquet.html)

- txt, txt.gz, txt.xz with `readLines`

- json, json.gz, json.xz with
  [`jsonlite::fromJSON`](https://jeroen.r-universe.dev/jsonlite/reference/fromJSON.html)

## See also

Other pb_rw:
[`guess_write_function()`](https://docs.ropensci.org/piggyback/reference/guess_write_function.md),
[`pb_read()`](https://docs.ropensci.org/piggyback/reference/pb_read.md),
[`pb_write()`](https://docs.ropensci.org/piggyback/reference/pb_write.md)
