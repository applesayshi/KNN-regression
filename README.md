# Predicting Player Engagement from Age — KNN vs. Linear Regression

Can a player's age predict how many hours they will contribute to PLAICraft, UBC's Minecraft research server? A comparison of KNN regression and simple linear regression in R.

**Report:** [KNN_regression_Project.pdf](KNN_regression_Project.pdf) · [HTML export](Final_Project%20FINAL.html)

## Data

`players.csv` from the Pacific Laboratory for Artificial Intelligence (PLAI): 196 registered players with experience level, age and total hours played. Only `age` (predictor) and `played_hours` (response) are used.

## Method

- Exploratory analysis of the age distribution and the age–hours relationship (right-skewed; most players are 0–25).
- **KNN regression** with `tidymodels`: 5-fold cross-validation over *k* to minimize RMSE.
- **Simple linear regression** on the same split.
- Compared both on held-out RMSPE.

## Results

| Model | Test RMSPE |
| --- | --- |
| KNN regression (best *k* = 82) | 39.58 |
| **Linear regression** | **39.20** |

Linear regression edges out KNN, and the KNN result is a red flag on its own: the best *k* is almost half the dataset, which means the model is underfitting rather than finding structure. The linear fit shows a weak negative relationship (slope −0.18 hours/year): older players contribute slightly fewer hours. Age alone is a poor predictor of engagement; the report discusses what additional features (experience level, session data) would help.

## Stack

R · `tidyverse` · `tidymodels` · `ggplot2` · `gridExtra`
