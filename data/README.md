# Data

The raw data is not stored in this repository because it is loaded directly in R using the `hoopR` package.

This project uses:

- NBA play-by-play data for the season labeled `2025`, corresponding to the 2024–2025 NBA season
- NBA player box-score data for the same season

The data is loaded in the Quarto analysis file using:

```r
nba_season <- 2025
nba_pbp <- hoopR::load_nba_pbp(seasons = nba_season)
box_scores <- hoopR::load_nba_player_box(nba_season)