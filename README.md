# 🚜 Bulldozer Price Regression
## Project Overview
* Created a tool that predicts (with an **RMSLE** score of 0.399) the sale price of bulldozers given its previous examples of how much similar bulldozers have been sold for. The resulted score would've gotten at least Based only on the model trained on a smaller portion of data than those in the leaderboard, we would place on the 91th position, thus earning a bronze medal 🥉.
* Trained models on a sample of around 400,000 examples with 50+ features (time series data with sale examples up to 2011). Validated the models on a sample of 12,000 examples (January 1 2012 to April 30 2012) and predicted the sale price target on a test sample of the same size.
* Experimented with RandomForestRegressor. Optimizations were done using RandomizedSearchCV in order to reach the best model.
## Code and Resources
* **Python Version**: 3.8.8
* **Packages**: pandas, numpy, sklearn, matplotlib, seaborn
* **Data Source**: https://www.kaggle.com/c/bluebook-for-bulldozers/overview
## Data Cleaning
After getting the data, I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:
* Parsed sale dates to datetime64 dtype.
* Sorted the data by sale dates.
* Added datetime parameters (saleYear, saleMonth, saleDay, saleDayOfWeek, saleDateOfYear) in order to find more possible patterns in our data then dropped the saledate column.
* Filled numerical missing values with median.
* Converted columns with strings to category, then encoded the categories (0 for missing values).
* Added binary columns to indicate whether sample had missing value.
