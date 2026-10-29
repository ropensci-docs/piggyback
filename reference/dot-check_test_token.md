# Check Test PAT

We use a fine-grained GitHub Personal Access Token in our auth testing.
This function is memoised and checks that the token has the correct
permissions to the various test repositories.

## Usage

``` r
.check_test_token()
```

## Value

named vector of TRUE or FALSE as to whether the token is configured and
can access the test repos.

## Details

It should have the following token permissions:

- Contents (read/write)

- Metadata (read)

on the following repositories

- tanho63/piggyback

- tanho63/piggyback-tests

- tanho63/piggyback-private (a private repository)
