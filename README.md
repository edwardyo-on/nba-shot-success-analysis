# NBA Shot Success Analysis

## Project Overview

This project analyzes NBA shot success during the 2024–2025 season using play-by-play and player box-score data from the `hoopR` package in R. The analysis compares shot volume, shot make rates, and model-based factors associated with made-shot probability.

The project focuses on two high-volume shot groups: layups and jump shots. For each group, standard logistic regression models are compared with mixed-effects logistic regression models that include player-level random intercepts.

## Research Questions

1. Which shot types account for the most made baskets?
2. Which shot types have the highest make rates among commonly attempted shots?
3. Which player and game-context variables are associated with layup and jump-shot success?
4. Do mixed-effects logistic regression models improve fit compared with standard logistic regression models?

## Tools Used

- R
- Quarto
- `hoopR`
- `tidyverse`
- `ggplot2`
- `gridExtra`
- `knitr`
- `lme4`
- `scales`
- Logistic regression
- Mixed-effects modeling
- AIC model comparison

## Project Structure

```text
nba-shot-success-analysis/
├── README.md
├── .gitignore
├── analysis/
│   └── nba-shot-success-analysis.qmd
├── data/
│   └── README.md
└── report/
    ├── nba-shot-success-analysis.html
    └── nba-shot-success-analysis.pdf
```

## Analysis Workflow

1. Load 2024–2025 NBA play-by-play data using `hoopR`.
2. Filter the dataset to shooting plays.
3. Identify the most common made-shot types.
4. Calculate make rates by shot type, filtering to commonly attempted shots.
5. Focus deeper analysis on layups and jump shots.
6. Filter layup attempts to reduce unusual or likely misclassified shot-location records.
7. Join shot-level play-by-play data with player box-score data.
8. Create modeling features such as shooting distance, field-goal percentage, three-point percentage, starter status, points scored, time remaining, and period number.
9. Fit standard logistic regression models for layups and jump shots.
10. Fit mixed-effects logistic regression models with player-level random intercepts.
11. Compare models using AIC.
12. Interpret model results, limitations, and possible future improvements.

## Key Findings

- The dataset includes 571,603 play-by-play events across 1,209 games from the 2024–2025 NBA season.
- Made-shot frequency and make rate answer different questions: made-shot frequency shows scoring volume, while make rate shows conversion efficiency.
- Layups and jump shots were selected for deeper modeling because they represent high-volume shot categories.
- Mixed-effects logistic regression had lower AIC than standard logistic regression for both layups and jump shots, suggesting that accounting for player-level differences improved relative model fit.
- Player efficiency metrics were associated with shot success in both layup and jump-shot models.
- Player-level random intercepts showed that individual shooting ability still matters after controlling for observable shot and game-context variables.
- Results should be interpreted as associations, not causal effects.

## Modeling Approach

The modeling portion compares two approaches for both layups and jump shots:

1. Standard logistic regression
2. Mixed-effects logistic regression with player-level random intercepts

The outcome variable is whether a shot was made. Logistic regression is used because the target variable is binary. The mixed-effects models account for repeated shot attempts by the same players, which helps avoid treating every shot attempt as fully independent.

AIC is used to compare model fit between the standard and mixed-effects models. Lower AIC values indicate better relative fit for models trained on the same outcome and dataset.

## Data Source

This project uses NBA play-by-play and player box-score data from the `hoopR` package.

The analysis uses the season labeled `2025` in `hoopR`, which corresponds to the 2024–2025 NBA season. The data includes regular season and postseason games.

Raw data files are not stored directly in this repository. The analysis loads the data through `hoopR` so the project can be reproduced from the source package.

## How to View the Report

Open the rendered HTML report:

```text
report/nba-shot-success-analysis.html
```

Or open the PDF report:

```text
report/nba-shot-success-analysis.pdf
```

## How to Reproduce

1. Install R and Quarto.

2. Install the required R packages:

```r
install.packages(c(
  "hoopR",
  "tidyverse",
  "ggplot2",
  "gridExtra",
  "knitr",
  "lme4",
  "scales"
))
```

3. Render the Quarto report:

```bash
quarto render analysis/nba-shot-success-analysis.qmd
```

4. Open the rendered report from the `report/` folder.

## Limitations

- The model does not include defender proximity, contest level, or defender identity.
- The model does not include shot-clock time, assist status, play type, or full possession context.
- Shot categories are broad and combine different subtypes, such as pull-up jumpers, fadeaways, driving layups, and cutting layups.
- The analysis uses one NBA season, so results may not generalize across seasons.
- AIC compares relative model fit but does not measure true out-of-sample predictive performance.
- The analysis is observational, so coefficients should be interpreted as associations rather than causal effects.

## Skills Demonstrated

This project demonstrates sports analytics, data cleaning, exploratory analysis, feature engineering, logistic regression, mixed-effects modeling, model comparison, Quarto reporting, and interpretation of statistical results.