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
1. Process the accumulated stats of each player for each game of the season
2. Processed data by each game, in which the columns are the stats of all of the starting players


## 3. Model training

**KoBERT tokenizer + Word2Vec + cosine-similarity**\
[Model train file (wv_model_train.ipynb)](./Model/wv_model_train.ipynb)

**KoBERT tokenizer:** Developed by SKTBrain\
**Word2Vec:** Represents words in vectors

**Model parameters:**\
vector dimension = 300, window = 8

**Model** [(Architecture.ipynb)](./Model/Architecture.ipynb)
- Added all word vectors in a news data to make a news representation
- Generated each theme representations by adding all 200 news representations
- Normalization was not necessary since more information leads to accurate representations
- When a news data is given as input, the model will vectorize the data and use cosine-similarity to determine and return the most similar theme

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

