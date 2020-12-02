# KBO: Predicting Baseball
Predicting ERA, match winner of each game in the KBO League

## Summary
* Data from KBO, open source
* Selected meaningful player stats/features in predicting game results.
* Processed dataset by each game/starting players
* Trained model with XGBoost, Bayesian Optimization

## 1. Background
### Why predict baseball?
* Baseball is one of the first sports to incorporate statistics, and is widely known for its usage of numbers and data when making decisions.
* By analyzing underlying correlations and implementing Machine Learning, it could be possible to predict the result of a baseball game.

## 2. Data preprocessing
### Player Stats
**Pitcher:** ERA, WHIP, K/BB ratio\
**Batter:** AVG, OBA, SLG


1. Process the accumulated stats of each player for each game of the season   [(notebook)](./data/individual_player_stats.ipynb)
2. Processed data by each game, in which the columns are the stats of all of the starting players   [(notebook)](./data/starting_stats.ipynb)
3. Finalized training data - stats of both Home and Away team's starting players for each match-up   [(notebook)](./data/create_dataset.ipynb)


## 3. Model training

**XGBoost + Bayesian Optimization**\
[ERA Predict Model](./model_era.ipynb)\
[Win Predict Model](./model_win.ipynb)

### Bayesian Optimization


## 4. Testing
**Model**
- **Input:** Today news(approximately 2000 data each for IT, economy, society, lifestyle, international, politics)
- **Output:** A list of themes and its subordinate corporations that are considered to have high potential
- The model finds a similar theme for each news data and counts the number of its appearance. However, it only counts when the similarity is higher than 95%.
- When all of the input data is processed, the model generates a list of themes, whose count is less than 5(hypothesis 3).

**Market testing**
- Select one corporation for each theme, whose fluctuation is less than 5% and has the highest market capitalization.
- Calculate profit with the following rules.
  - Sell when a stock's price increases more than 10%
  - Sell when a stock's price decreases more than 5%
  - If neither of above, sell after 5 days of purchase
  
**Result**

