# Linear Regression
Today you will learn about linear regression and how we can use it to view sports with a more analytical mindset. 

## What is Linear Regression?
Linear Regression models use multiple independent variables to predict the value of a dependent continuous variable (passing yards, goals scored, shots made). <br> 

## Today's Model
The model you will be making today uses NFL passing data from 2016 to 2024. At the end, you will be able to predict the passing stats for the 2026 season and have a good understanding of what linear regression is used for. <br>

**Open GitHub Desktop and then open the repo in VS Code.** <br>

At the top of all of these notebooks, there will be a cell that looks like this: <br>

```python
import pandas as pd
import numpy as np
import statsmodels.api as sm 
from statsmodels.stats.outliers_influence import variance_inflation_factor
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
```

These are just tools that will help you construct and view your model. If you get a 'no module named ___ ' error, insert whatever it says your missing in the blank and run something like this: <br>

```python
# if this one doesn't work, try the others
pip install _____

%pip install _____
!pip install _____

```

The notebooks will also always contain a line that reads the data from a CSV that looks like this: <br>

```python
df = pd.read_csv('qb_data.csv')
```

## What is VIF?
In one of the cells, there is code that outputs VIF values. VIF (Variance Inflation Factor) tells us if two or more variables are highly correlated. For example, if you had a housing dataset that contained variables like # of rooms, total square feet, and whether it has a basement or not, both # of rooms and total square feet would have high VIF values because usually properties with higher square feet have more rooms. You would see this in sports with stats like passing yards/completions, shots on goal/goals, and shots/points. **You want to try and keep your VIF values below 5.**<br>

## How do you Interpret a Model Output?
In the next cell, there is code that prints a model output. There is lots of good information here, but the three main pieces are the coefficients, P-values, and R-squared values. The coefficients tell us how important each feature was, the P-values indicate how statistically significant each feature is, and the R-squared value tells you how "good" your model is. A feature is statistically significant if its P-value is less than 0.05. Your model is pretty good if your R-squared value is between 0.4 and 0.6, but you always want to be as close to 1.0 as possible. <br>

## What is RMSE?
RMSE (Root Mean Squared Error) is the window of error that you should provide your predictions. For example, if your RMSE is eight and our model predicts Bryce Young to throw 24 touchdowns, it would be better to say that the model predicts Bryce Young to throw somewhere between 16 and 32 touchdowns, which is a very large window, but it explains why the model's R-squared is so low. <br>
Your model is adding something if the RMSE is less than the standard deviation in the feature you are predicting. Run **df.describe()** to find the standard deviation.

## What does the Math Look Like?
The formula for predicting by hand is *intercept + (variable 1 * var 1 coef) + (variable 2 * var 2 coef)...* <br>
The model output gives you all the information needed to perform this calculation. 

## Why are the Predictions Low?
The model's predictions seem a little bit low, lets take a look at this graph: <br>

![p_tds.png](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/p_tds.png)

The graph shows us that it is much more common for a player to throw 0-25 touchdowns than it is for a player to throw 26-50, which explains why the model's predictions are low. 

