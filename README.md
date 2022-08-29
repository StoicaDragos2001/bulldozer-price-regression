# 🚜 Bulldozer Price Regression
## Project Overview
* Created a tool that predicts (with an **RMSLE** score of 0.399) the sale price of bulldozers given its previous examples of how much similar bulldozers have been sold for. Based only on the model trained on a smaller portion of data than those in the leaderboard, we would place on the 91th position, thus earning a bronze medal 🥉.
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
## EDA
I looked at the relationships between certain features found in our data. Below are a few highlights from the analysis made.
![download](https://user-images.githubusercontent.com/79250297/187257951-ef55f810-8077-492f-890b-1ff776e07680.png)
![download](https://user-images.githubusercontent.com/79250297/187258159-18fa8653-dabc-479e-9eb0-2e1aef197525.png)
## Model Building
The data was split based on sale date: the training set contains past sale data of bulldozers up to 2011, the validation set has data from January 1 2012 to April 30 2012, and the test set is based on the remaining data.

I tried training a Random Forest Regressor model because it can handle large datasets efficiently and it would minimize the time between experiments on this amount of data.
## Model Performance 
After experimenting with a max_sample of 10000 and using RandomizedSearchCV for hyperparamater tuning, i retrained the model on the whole training dataset, getting a RMSLE(root mean square log error) score of 0.399 on the validation dataset.
A feature importance figure is shown below.
![download](https://user-images.githubusercontent.com/79250297/187263216-f41c7e65-cc51-4261-b8a3-94f768a8bf2d.png)

