# piggyback: Managing Larger Data on a GitHub Repository

Because larger (\> 50 MB) data files cannot easily be committed to git,
a different approach is required to manage data associated with an
analysis in a GitHub repository. This package provides a simple
work-around by allowing larger (up to 2 GB) data files to piggyback on a
repository as assets attached to individual GitHub releases. These files
are not handled by git in any way, but instead are uploaded, downloaded,
or edited directly by calls through the GitHub API. These data files can
be versioned manually by creating different releases. This approach
works equally well with public or private repositories. Data can be
uploaded and downloaded programmatically from scripts. No authentication
is required to download data from public repositories.

## See also

Useful links:

- <https://docs.ropensci.org/piggyback/>

- <https://github.com/ropensci/piggyback>

- Report bugs at <https://github.com/ropensci/piggyback/issues>

## Author

**Maintainer**: Carl Boettiger <cboettig@gmail.com>
([ORCID](https://orcid.org/0000-0002-1642-628X)) \[copyright holder\]

Authors:

- Tan Ho ([ORCID](https://orcid.org/0000-0001-8388-5155))

Other contributors:

- Mark Padgham ([ORCID](https://orcid.org/0000-0003-2172-5265))
  \[contributor\]

- Jeffrey O Hanson ([ORCID](https://orcid.org/0000-0002-4716-6134))
  \[contributor\]

- Kevin Kuo ([ORCID](https://orcid.org/0000-0001-7803-7901))
  \[contributor\]
