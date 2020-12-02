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

- Searches the best parameters within the specified range
- ex)


  ```
  XGB_BO = BayesianOptimization(XGB_CV, {
                                      'max_depth': (2, 12),
                                      'gamma': (0.001, 10.0),
                                      'min_child_weight': (0, 20),
                                      'max_delta_step': (0, 10),
                                      'subsample': (0.4, 1.0),
                                      'colsample_bytree' :(0.4, 1.0),
                                      'eta' : (0.01, 0.3)
                                      })
  ```

## 4. Testing
**ERA**
- RMSE: 2.858035
- R2: 0.021920

**WIN**
- Score: 0.5787671232876712


