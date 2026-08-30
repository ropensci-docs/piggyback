# Changelog

## piggyback (development version)

- Fix bug in
  [`pb_releases()`](https://docs.ropensci.org/piggyback/reference/pb_releases.md)
  to allow for draft releases to appear \[#105\]
- [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  no longer offers to create a release if interactive - it now provides
  the code to create the release in the error body.
- [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md)
  now tries to uses browser download URLs
  (i.e. [`pb_download_url()`](https://docs.ropensci.org/piggyback/reference/pb_download_url.md))
  before trying API download URLs. This should reduce/eliminate effect
  of API rate limits for pb_download. \[#109\]
- `"latest"` release now aligns with GitHub’s “latest” release
  definition \[#113\]
- [`pb_download_url()`](https://docs.ropensci.org/piggyback/reference/pb_download_url.md)
  now can return choice of “browser” or “api” download URLs \[#116\]
- Add new functions
  [`pb_read()`](https://docs.ropensci.org/piggyback/reference/pb_read.md)
  and
  [`pb_write()`](https://docs.ropensci.org/piggyback/reference/pb_write.md)
  as convenience wrappers around pattern of downloading to
  [`tempfile()`](https://rdrr.io/r/base/tempfile.html) and then reading
  into memory. \[#97\]
- Support customizing GitHub base URL via GITHUB_API_URL environment
  variable, which should help support GH Enterprise \[#122\]
- Fix bug in `pb_info()` when GitHub releases are duplicated.

## piggyback 0.1.5

CRAN release: 2023-07-10

- Fix bug in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  to correctly resolve `"latest"` tag - if there is no release tag
  actually named “latest” it will use the first release from
  [`pb_releases()`](https://docs.ropensci.org/piggyback/reference/pb_releases.md).
  \[#75\]
- Make
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md)
  and `pb_info()` also resolve `"latest"` similarly: if there is no
  release tag named “latest”, use first release from
  [`pb_releases()`](https://docs.ropensci.org/piggyback/reference/pb_releases.md)
- Updated test coverage to use GHA
- Fixed error handling for
  [`pb_list()`](https://docs.ropensci.org/piggyback/reference/pb_list.md)
  for no release.
- [`pb_list()`](https://docs.ropensci.org/piggyback/reference/pb_list.md)
  now respects the option `"piggyback.verbose"`
- Fix download token handling \[#88\]
- [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  no longer prints out extra newlines \[#93\]
- [`pb_new_release()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  now warns and exits early instead of failing if a release already
  exists. \[#95\]
- Fixup test issues \[#100\]
- `pb_upload` adds a two-second sleep after user creates release
  \[#101\]
  - This is because it takes a few seconds for the GitHub API to
    register that the new release has been created
- Adds `piggyback.cache` R option to avoid memoising altogether
- Adds
  [`.pb_cache_clear()`](https://docs.ropensci.org/piggyback/reference/dot-pb_cache_clear.md)
  function to empty the cache more consistently (internally and
  externally)

## piggyback 0.1.4

CRAN release: 2022-07-19

- The progress bar argument `show_progress` in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  and
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md)
  now defaults to
  [`interactive()`](https://rdrr.io/r/base/interactive.html) \[#72\]
- Fix bug in
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md)
  for downloading without a
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)
  (mostly on Windows?) \[#77\]
- Fix bug introduced by above bugfix - missed Authorization in header
- `guess_repo()` now uses
  [`gh::gh_tree_remote()`](https://gh.r-lib.org/reference/gh_tree_remote.html)
  rather than gert - this eliminates the gert dependency. \[#80\]
- [`pb_release_delete()`](https://docs.ropensci.org/piggyback/reference/pb_release_delete.md)
  introduced to delete existing releases. \[#81\]
- [`pb_new_release()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  renamed to
  [`pb_release_create()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  to sync with the new delete function.
- Fix offer to create new release in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md) -
  also switch to using
  [`rlang::is_interactive()`](https://rlang.r-lib.org/reference/is_interactive.html)
  to maybe one day test this.
- Tests rewritten to primarily use GHA and write to/from the
  ropensci/piggyback repo.
- Added [`httr::RETRY()`](https://httr.r-lib.org/reference/RETRY.html)
  behaviour to
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md).

## piggyback 0.1.3

CRAN release: 2022-05-19

- fix bug in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  for uploading to a release with no assets \[#67\]
- avoid implicit dependency on `tibble` \[#70\]

## piggyback 0.1.2

CRAN release: 2022-04-26

- update intro vignette to remove all mentions of `pb_track()`,
  `pb_push()`, and `pb_pull()` which were removed as of version
  0.0.0.9900
- [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  now handles the `dir` argument to control relative path directories.
- update intro vignette to remove mention of path name handling and
  instead provide examples of how path names are handled.
- update intro vignette instructions for git authentication
- [`pb_new_release()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  now reports HTTP errors when attempting to create a new release and
  returns the contents of the error if it fails.
- [`pb_releases()`](https://docs.ropensci.org/piggyback/reference/pb_releases.md)
  created - it returns a list of releases available in the repository.
- Internal function `pb_info()` refactored to search for the specified
  tag(s) which should improve performance. Should handle multiple tags
  gracefully.
- Internal function `pb_info()` (and therefore
  [`pb_list()`](https://docs.ropensci.org/piggyback/reference/pb_list.md),
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md),
  [`pb_download_url()`](https://docs.ropensci.org/piggyback/reference/pb_download_url.md))
  no longer ask about creating new releases if the release is not found.
- [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  is now the only function that offers (interactively) to create a new
  release if release is not found. If noninteractive, user must run
  [`pb_new_release()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  manually prior to uploading.
- CLI messaging now consistently uses [cli](https://cli.r-lib.org)
  package and no longer uses clisymbols or crayon - this is to align
  with the imports from the [gh](https://gh.r-lib.org/) package.
- Documentation updated.
- Add options(“piggyback.verbose”) TRUE/FALSE to control
  verbosity/messaging levels.

## piggyback 0.1.1

CRAN release: 2021-09-09

- switch to gh::gh_token() for token management. Still supports the same
  env var approach, but also compatible with `gitcreds` and other use.
- resolve issue in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  when creating a new tag in the process, previously data would be
  attached to the previously `latest` tag instead of the newly created
  one.
- resolve issue in
  [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md)
  where httr would report a 401 status even after data successfully
  downloads.

## piggyback 0.1.0

CRAN release: 2021-08-06

- address remaining authentication issue in changes to GitHub API (on
  pb_upload()) \[#47\]
- Use flat file structure on upload/download instead of encoding path
  \[#48\]
- improve performance via more aggressive memoising of `pb_info()`
  calls, inceasing default `piggyback_cache_duration` to 10 minutes
  \[#46\]
- Resolve bug introduced by API changes that would stop creation of tags
  on repos with default branch called `main` or without previous
  releases \[#48\]

## piggyback 0.0.12

- address issues in authentication due to changes in GitHub API
  ([\#37](https://github.com/ropensci/piggyback/issues/37))

## piggyback 0.0.11 2020-02-25

CRAN release: 2020-02-25

- `guess_repo()` now infers a remote when there are multiple associated
  with the repo. The “upstream” (preferred) or “origin” repo is selected
  if either exists, otherwise the function errors and asks the user to
  explicitly specify a repo
  ([\#31](https://github.com/ropensci/piggyback/issues/31)).
- `release_info()` now works properly when there are no existing
  releases, which enables the usage of
  [`pb_new_release()`](https://docs.ropensci.org/piggyback/reference/pb_release_create.md)
  on repos without a release
  ([\#29](https://github.com/ropensci/piggyback/issues/29)).
- Fix error on `pb_info()` under certain cases which resulted in
  `Error in a[[1]] : subscript out of bounds`,
  ([\#36](https://github.com/ropensci/piggyback/issues/36))
- Fix CRAN unit-test on deleting file

## piggyback 0.0.10 2018-02-06

CRAN release: 2019-02-07

- Improve interface regarding `overwrite` behavior in
  [`pb_upload()`](https://docs.ropensci.org/piggyback/reference/pb_upload.md)
  ([\#25](https://github.com/ropensci/piggyback/issues/25))
- Bugfixes for errors introduced in 0.0.9:
  - Access all assets on a release instead of first 30. This could break
    upload and download.
    ([\#23](https://github.com/ropensci/piggyback/issues/23),
    [\#24](https://github.com/ropensci/piggyback/issues/24))
  - Uploading of directory paths could cause download errors in
    [`pb_download()`](https://docs.ropensci.org/piggyback/reference/pb_download.md).
    ([\#24](https://github.com/ropensci/piggyback/issues/24),
    [\#26](https://github.com/ropensci/piggyback/issues/26))

## piggyback 0.0.9, 2019-01-08

CRAN release: 2019-01-08

- Enable re-upload and deletion of partially uploaded files
  ([\#19](https://github.com/ropensci/piggyback/issues/19))

## piggyback 0.0.8, 2018-10-06

CRAN release: 2018-10-06

- Updates to documentation, streamlining tests
- remove dependency on
  [`utils::askYesNo`](https://rdrr.io/r/utils/askYesNo.html) which is
  only available in R \>= 3.5.0

## piggyback 0.0.7, 2018-09-30

CRAN release: 2018-09-30

- Initial release to CRAN

------------------------------------------------------------------------

## piggyback 0.0.6, 2018-09-21

- bugfix for migrating unit test

## piggyback 0.0.6, 2018-09-21

- bugfix for migrating unit test, JOSS submission

## piggyback 0.0.5, 2018-09-21

- initial Onboarding to rOpenSci

## piggyback 0.0.0.9000

- Added a `NEWS.md` file to track changes to the package.
