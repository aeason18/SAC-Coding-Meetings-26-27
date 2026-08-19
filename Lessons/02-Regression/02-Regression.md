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
In one of the cells, there is code that outputs VIF values. VIF (Variance Inflation Factor) tells us if 2 or more variables are highly correlated. For example, if you had a housing dataset that contained variables like # of rooms, total square feet, and whether it has a basement or not, both # of rooms and total square feet would have high VIF values because usually properties with higher square feet have more rooms. You would see this in sports with stats like passing yards/completions, shots on goal/goals, and shots/points. <br>


