# Lesson 4: Decision Trees
A Decision Tree is a classification model that can handle predicting both binary and categorical data. 

## Today's Model
The model you will be making today uses data from the 2025 NFL season to predict whether a play will be a run or a pass. <br>

**Open GitHub Desktop and then open the repo in VS Code (Make sure to pull any changes that have been made to the online repo).** <br>

At the top of the notebook, you will see the packages you will use, the import statement, and a preview of the table. <br>

## Defining X and y & Model Training/Fitting 
The column names are missing for both statements where X and y are defined. X is what we are using to predict y, so for X, drop all the columns that won't help us predict y. For y, we need what we are predicting, which is whether the play is a run or pass, so choose the corresponding features and place them within the brackets for X and y in this cell: <br>

```python
# set up variables (what coulmns are not needed for predicting our target variable)
X = df.drop(columns=[])
y = df[]
```

After that, we must split our data into training and testing data, in our last in-person lesson, we briefly talked ```train_test_split()``` which is a method that randomly separates our data for us, so fill in the blank in this cell with ```train_test_split()```: <br>

```python
# breakup training and testing data (do you remember the data split method we briefly talked about last time)
# test_size = 0.2 means that we are saving a random 20% of our data for testing and using the other 80% for training.
X_train, X_test, y_train, y_test = ###########(X, y, test_size=0.2, random_state=42)
```
