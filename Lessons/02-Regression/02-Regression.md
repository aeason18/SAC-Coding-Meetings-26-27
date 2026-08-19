# Linear Regression
Today you will learn about linear regression and how we can use it to view sports with a more analytical mindset. 

## What is Linear Regression?
Linear Regression models use multiple independent variables to predict the value of a dependent continuous variable (passing yards, goals scored, shots made). <br> 

## Today's Model
The model you will be making today uses NFL passing data from 2016 to 2024. At the end, you will be able to predict the passing stats for the 2026 season and have a good understanding of what linear regression is used for. <br>

At the top of all of our notebooks, there will be a cell that looks like this: <br>

```python
import pandas as pd
import numpy as np
import statsmodels.api as sm 
from statsmodels.stats.outliers_influence import variance_inflation_factor
from sklearn.metrics import mean_squared_error
import matplotlib.pyplot as plt
```

These are just tools that will help us construct and view our model. If you get a 'no module named ___ ' error, insert whatever it says your missing in the blank and run something like this: <br>

```python
# if this one doesn't work, try the others
pip install _____

%pip install _____
!pip install _____

```

