# piggyback

`piggyback` provides an R interface for storing files as GitHub release
assets, which is a convenient way for large/binary data files to
*piggyback* onto public and private GitHub repositories. This package
includes functions for file downloads, uploads, and managing releases,
which then are passed to the GitHub API.

No authentication is required to download data from public repositories.

## Installation

Install from CRAN via:

``` r

install.packages("piggyback")
```

You can install the development version from
[GitHub](https://github.com/ropensci/piggyback) with either r-universe
or with remotes:

``` r

install.packages("piggyback", repos = c('https://ropensci.r-universe.dev', getOption("repos")))
# install.packages("remotes")
remotes::install_github("ropensci/piggyback")
```

## Usage

See [getting started
vignette](https://docs.ropensci.org/piggyback/articles/piggyback.html)
for a more comprehensive introduction.

Download data attached to a GitHub release:

``` r

library(piggyback)
pb_download("iris2.tsv.gz", 
            repo = "cboettig/piggyback-tests",
            tag = "v0.0.1",
            dest = tempdir())
#> ℹ Downloading "iris2.tsv.gz"...
#> |======================================================| 100%
fs::dir_tree(tempdir())
#> /tmp/RtmpWxJSZj
#> └── iris2.tsv.gz
```

Downloading from private repos or uploading to any repo requires
authentication, specifically a GitHub Personal Access Token (PAT). This
can be stored as a
[gh::gh_token()](https://usethis.r-lib.org/articles/git-credentials.html#get-a-personal-access-token-pat)
or a GITHUB_PAT environment variable - for more information, see the
vignette notes on
[authentication](https://docs.ropensci.org/piggyback/articles/piggyback.html#authentication).

We can also upload data to a release. Start by creating a release:

``` r

pb_release_create(repo = "cboettig/piggyback-tests", tag = "v0.0.2")
#> ✔ Created new release "v0.0.2".
```

then upload to it:

``` r

readr::write_tsv(mtcars, "mtcars.tsv.gz")
pb_upload("mtcars.tsv.gz", repo = "cboettig/piggyback-tests")
#> ℹ Uploading to latest release: "v0.0.2".
#> ℹ Uploading mtcars.tsv.gz ...
#> |===================================================| 100%
```

For improved performance, we can also use piggyback files with [cloud
native](https://docs.ropensci.org/piggyback/articles/cloud_native.html)
workflows to query data without downloading it first.

## Motivations

A brief video overview presented as part of Tan Ho’s [RStudioConf2022
talk](https://www.youtube.com/watch?v=wzcz4xNGeTI&t=655s):

<https://github.com/ropensci/piggyback/assets/38083823/a1dff640-1bba-4c06-bad2-feda34f47387>

`piggyback` allows you to store data alongside your repository as
release assets, which helps you:

- store files larger than 50MB
- bypass the 2GB GitHub repo size limit
- avoid the [downsides](https://archive.is/3D16r) of Git LFS
- version data flexibly (by creating/uploading to a new release)
- work with public and private repositories, **for free**

For more about motivations, see this discussion of
[alternatives](https://docs.ropensci.org/piggyback/articles/alternatives.html).

## Contributing

Please note that this project is released with a [Contributor Code of
Conduct](https://ropensci.org/code-of-conduct/). By participating in
this project you agree to abide by its terms.
