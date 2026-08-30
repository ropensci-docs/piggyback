# List releases in repository

This function retrieves information about all releases attached to a
given repository.

## Usage

``` r
pb_releases(
  repo = guess_repo(),
  .token = gh::gh_token(),
  verbose = getOption("piggyback.verbose", default = TRUE)
)
```

## Arguments

- repo:

  GitHub repository specification in the form of `"owner/repo"`, if not
  specified will try to guess repo based on current working directory.

- .token:

  a GitHub API token, defaults to
  [`gh::gh_token()`](https://gh.r-lib.org/reference/gh_token.html)

- verbose:

  defaults to TRUE, use FALSE to silence messages

## Value

a dataframe of all releases available within a repository.

## Examples

``` r
# \donttest{
try({ # wrapped in try block to prevent CRAN errors
 pb_releases("nflverse/nflverse-data")
})
#> ⠙ 25 items, page 1 | 2ms
#>            release_name release_id
#> 1                trades  251527510
#> 2                 teams  251328051
#> 3             schedules  251386473
#> 4    Team Summary Stats  236670540
#> 5  Player Summary Stats  236670328
#> 6          ftn_charting  119740650
#> 7             espn_data  121931789
#> 8        weekly_rosters   73313637
#> 9    players_components  109160206
#> 10              players   69785162
#> 11    pbp_participation   71636554
#> 12            officials   69773595
#> 13                 misc   69471165
#> 14                 test   66262662
#> 15          draft_picks   66254658
#> 16            contracts   65273753
#> 17          snap_counts   58153010
#> 18              rosters   58152863
#> 19         player_stats   58152881
#> 20         pfr_advstats   58152981
#> 21                  pbp   58152862
#> 22        nextgen_stats   58152931
#> 23             injuries   58152949
#> 24         depth_charts   58152948
#> 25              combine   60901499
#>                                                                                                                                                                                                                                                                                                                                                                                                                                                                     release_body
#> 1                                                                                                                                                                                                                                                                                                              data is maintained by Lee Sharpe here https://github.com/nflverse/nfldata/blob/master/data/trades.csv and automated to push common data formats into this release
#> 2  NFL team names, colors, logo urls, and more.\r\n\r\nDocumented in [nflfastR](https://www.nflfastr.com/reference/teams_colors_logos.html). \r\nAccess with\r\n```r\r\nnflreadr::load_teams()\r\n```\r\nor\r\n```python\r\nimport nflreadpy as nfl\r\nnfl.load_teams()\r\n```\r\n\r\nData maintained in [nflverse-pbp](https://github.com/nflverse/nflverse-pbp/blob/master/teams_colors_logos.csv). \r\nData in this release updates automatically if the linked file changes.
#> 3              NFL game/schedule data.\r\n\r\nDocumented in [nflreadr](https://nflreadr.nflverse.com/articles/dictionary_schedules.html). \r\nAccess with\r\n```r\r\nnflreadr::load_schedules()\r\n```\r\nor\r\n```python\r\nimport nflreadpy as nfl\r\nnfl.load_schedules()\r\n```\r\n\r\nData maintained in [Lee Sharpe's nfldata](https://github.com/nflverse/nfldata/blob/master/data/games.rds). \r\nData in this release updates automatically if the linked file changes.
#> 4                                                                                                                                                                                                                                                                                                                                                                                              Team stats in different summary levels created with `nflfastR::calculate_stats()`
#> 5                                                                                                                                                                                                                                                                                                                                                                                            Player stats in different summary levels created with `nflfastR::calculate_stats()`
#> 6                                                                                                                                                                                                                                                                                                                                                                                                                          Charting data provided by https://FTNFantasy.com/data
#> 7                                                                                                                                                                                                                                                                                                                                                                                                                                                                     ESPN Stats
#> 8                                                                                                                                                                                                                                                                                                                                                                                                                Week-level rosters via NFL Shield v2 API, dating back to 2002. 
#> 9                                                                                                                                                                                                                                                                                                                                                                                                                                     Component files for nflverse players build
#> 10                                                                                                                                                                                                                                                                                                                                                                        Player information for nflverse. This should be the go-to for position and ID mappings going forward. 
#> 11                                                                                                                                                                                                                                                                                                                                                                                                                                         Participation data for plays from NGS
#> 12                                                                                                                                                                                                                                                                                                                                                                                                     Data about which referees and officials were assigned to specific games. 
#> 13                                                                                                                                                                                                                                                                          Various bits of data stored here as onetime jobs. Not automatically updated. Please file an issue or mention it on discord if you'd like to request something be maintained on an automatic schedule
#> 14                                                                                                                                                                                                                                                                                                                                                                                                                                                          for internal testing
#> 15                                                                                                                                                                                                                                                                                                                                 Draft picks dating back to 1980, courtesy of Pro Football Reference. \r\n\r\nIncludes some career-level and ApproxValue/HOF/MVP/PB stats.\r\n
#> 16                                                                                                                                                                                                                                                                                                                                                                                                         OverTheCap contract data, accessed with `nflreadr::load_contracts()`.
#> 17                                                                                                                                                                                                                                                                                                                                                                               Snap counts data, accessed with `nflreadr::load_snap_counts()`.\r\n\r\nLast Updated: 2022-03-06
#> 18                                                                                                                                                                                                                                                                                                                                                                                                                         Roster data, accessed with `nflreadr::load_rosters()`
#> 19                                                                                                                                                                                                                                                                                                                                                                                                             DEPRECATED 2025-08-01: USE `stats_player` OR `stats_team` INSTEAD
#> 20                                                                                                                                                                                                                                                                                                                                                                                                 PFR Adv Stats data, accessed with `nflreadr::load_pfr_advstats()`\r\n\r\n\r\n
#> 21                                                                                                                                                                                                                                                                                                                                                                                                                       Play by play data, accessed with `nflreadr::load_pbp()`
#> 22                                                                                                                                                                                                                                                                                                                                                                                                       NFL Next Gen Stats data, accessed with `nflreadr::load_nextgen_stats()`
#> 23                                                                                                                                                                                                                                                                                                                                                                                                                      Injuries data, accessed with `nflreadr::load_injuries()`
#> 24                                                                                                                                                                                                                                                                                                                                                                                                               Depth chart data, accessed with `nflreadr::load_depth_charts()`
#> 25                                                                                                                                                                                                                       NFL Combine Data courtesy of PFR, accessed with `nflreadr::load_combine()`. \r\n\r\nYou may also be interested in tanho63/nfl_combine for the (manual) nfl.com data version, which might eventually get moved into this release if we can automate it. 
#>              tag_name draft latest           created_at         published_at
#> 1              trades FALSE  FALSE 2025-10-01T03:03:35Z 2025-10-01T18:24:36Z
#> 2               teams FALSE  FALSE 2025-10-01T03:03:35Z 2025-10-01T06:42:54Z
#> 3           schedules FALSE  FALSE 2025-10-01T03:03:35Z 2025-10-01T11:19:34Z
#> 4          stats_team FALSE  FALSE 2025-07-01T03:22:45Z 2025-07-31T18:48:46Z
#> 5        stats_player FALSE  FALSE 2025-07-01T03:22:45Z 2025-07-31T18:47:44Z
#> 6        ftn_charting FALSE  FALSE 2023-09-01T02:16:48Z 2023-09-03T16:14:36Z
#> 7           espn_data FALSE  FALSE 2023-09-01T02:16:48Z 2023-09-20T19:50:55Z
#> 8      weekly_rosters FALSE  FALSE 2022-06-15T16:58:26Z 2022-08-01T07:45:30Z
#> 9  players_components FALSE  FALSE 2022-06-15T16:58:26Z 2023-06-20T01:22:44Z
#> 10            players FALSE  FALSE 2022-06-15T16:58:26Z 2022-06-19T05:36:22Z
#> 11  pbp_participation FALSE  FALSE 2022-06-15T16:58:26Z 2022-07-10T04:32:49Z
#> 12          officials FALSE  FALSE 2022-06-15T16:58:26Z 2022-06-18T17:47:11Z
#> 13               misc FALSE  FALSE 2022-05-29T16:57:43Z 2022-06-14T23:46:04Z
#> 14               test FALSE  FALSE 2022-05-06T19:04:21Z 2022-05-06T19:56:46Z
#> 15        draft_picks FALSE  FALSE 2022-05-06T18:12:18Z 2022-05-06T18:15:12Z
#> 16          contracts FALSE  FALSE 2022-03-21T14:03:51Z 2022-04-25T19:40:32Z
#> 17        snap_counts FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:15:02Z
#> 18            rosters FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:12:10Z
#> 19       player_stats FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:12:36Z
#> 20       pfr_advstats FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:14:24Z
#> 21                pbp FALSE   TRUE 2022-01-28T02:09:45Z 2022-01-28T02:12:09Z
#> 22      nextgen_stats FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:13:25Z
#> 23           injuries FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:13:49Z
#> 24       depth_charts FALSE  FALSE 2022-01-28T02:09:45Z 2022-01-28T02:13:47Z
#> 25            combine FALSE  FALSE 2022-01-28T02:09:45Z 2022-03-03T15:51:29Z
#>                                                                     html_url
#> 1              https://github.com/nflverse/nflverse-data/releases/tag/trades
#> 2               https://github.com/nflverse/nflverse-data/releases/tag/teams
#> 3           https://github.com/nflverse/nflverse-data/releases/tag/schedules
#> 4          https://github.com/nflverse/nflverse-data/releases/tag/stats_team
#> 5        https://github.com/nflverse/nflverse-data/releases/tag/stats_player
#> 6        https://github.com/nflverse/nflverse-data/releases/tag/ftn_charting
#> 7           https://github.com/nflverse/nflverse-data/releases/tag/espn_data
#> 8      https://github.com/nflverse/nflverse-data/releases/tag/weekly_rosters
#> 9  https://github.com/nflverse/nflverse-data/releases/tag/players_components
#> 10            https://github.com/nflverse/nflverse-data/releases/tag/players
#> 11  https://github.com/nflverse/nflverse-data/releases/tag/pbp_participation
#> 12          https://github.com/nflverse/nflverse-data/releases/tag/officials
#> 13               https://github.com/nflverse/nflverse-data/releases/tag/misc
#> 14               https://github.com/nflverse/nflverse-data/releases/tag/test
#> 15        https://github.com/nflverse/nflverse-data/releases/tag/draft_picks
#> 16          https://github.com/nflverse/nflverse-data/releases/tag/contracts
#> 17        https://github.com/nflverse/nflverse-data/releases/tag/snap_counts
#> 18            https://github.com/nflverse/nflverse-data/releases/tag/rosters
#> 19       https://github.com/nflverse/nflverse-data/releases/tag/player_stats
#> 20       https://github.com/nflverse/nflverse-data/releases/tag/pfr_advstats
#> 21                https://github.com/nflverse/nflverse-data/releases/tag/pbp
#> 22      https://github.com/nflverse/nflverse-data/releases/tag/nextgen_stats
#> 23           https://github.com/nflverse/nflverse-data/releases/tag/injuries
#> 24       https://github.com/nflverse/nflverse-data/releases/tag/depth_charts
#> 25            https://github.com/nflverse/nflverse-data/releases/tag/combine
#>                                                                                        upload_url
#> 1  https://uploads.github.com/repos/nflverse/nflverse-data/releases/251527510/assets{?name,label}
#> 2  https://uploads.github.com/repos/nflverse/nflverse-data/releases/251328051/assets{?name,label}
#> 3  https://uploads.github.com/repos/nflverse/nflverse-data/releases/251386473/assets{?name,label}
#> 4  https://uploads.github.com/repos/nflverse/nflverse-data/releases/236670540/assets{?name,label}
#> 5  https://uploads.github.com/repos/nflverse/nflverse-data/releases/236670328/assets{?name,label}
#> 6  https://uploads.github.com/repos/nflverse/nflverse-data/releases/119740650/assets{?name,label}
#> 7  https://uploads.github.com/repos/nflverse/nflverse-data/releases/121931789/assets{?name,label}
#> 8   https://uploads.github.com/repos/nflverse/nflverse-data/releases/73313637/assets{?name,label}
#> 9  https://uploads.github.com/repos/nflverse/nflverse-data/releases/109160206/assets{?name,label}
#> 10  https://uploads.github.com/repos/nflverse/nflverse-data/releases/69785162/assets{?name,label}
#> 11  https://uploads.github.com/repos/nflverse/nflverse-data/releases/71636554/assets{?name,label}
#> 12  https://uploads.github.com/repos/nflverse/nflverse-data/releases/69773595/assets{?name,label}
#> 13  https://uploads.github.com/repos/nflverse/nflverse-data/releases/69471165/assets{?name,label}
#> 14  https://uploads.github.com/repos/nflverse/nflverse-data/releases/66262662/assets{?name,label}
#> 15  https://uploads.github.com/repos/nflverse/nflverse-data/releases/66254658/assets{?name,label}
#> 16  https://uploads.github.com/repos/nflverse/nflverse-data/releases/65273753/assets{?name,label}
#> 17  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58153010/assets{?name,label}
#> 18  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152863/assets{?name,label}
#> 19  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152881/assets{?name,label}
#> 20  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152981/assets{?name,label}
#> 21  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152862/assets{?name,label}
#> 22  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152931/assets{?name,label}
#> 23  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152949/assets{?name,label}
#> 24  https://uploads.github.com/repos/nflverse/nflverse-data/releases/58152948/assets{?name,label}
#> 25  https://uploads.github.com/repos/nflverse/nflverse-data/releases/60901499/assets{?name,label}
#>    n_assets
#> 1         7
#> 2         7
#> 3         7
#> 4       542
#> 5       542
#> 6        18
#> 7        12
#> 8       104
#> 9        12
#> 10        7
#> 11       46
#> 12        7
#> 13       17
#> 14        5
#> 15        7
#> 16        7
#> 17       73
#> 18      434
#> 19     1822
#> 20      190
#> 21      160
#> 22       95
#> 23       73
#> 24      109
#> 25        7
# }
```
