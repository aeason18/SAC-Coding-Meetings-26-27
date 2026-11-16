# XGBoost
XGBoost is a machine learning algorithm that uses a sequence of decision trees with weighted data to help improve prediction accuracy. Check the slides in the folder on the main page for a nice graphic to help with your understanding.

## Today's Model
The model you will be making today uses data from the 2025 NFL season to predict a team's win chance throughout a game. <br>

**Open GitHub Desktop and then open the repo in VS Code (Make sure to pull any changes that have been made to the online repo).** <br>

At the top of the notebook, you will see the packages you will use and a preview of the table. Today, the CSV was too big to upload to GitHub, so download it from the link below. <br>

Link to CSV: https://drive.google.com/drive/folders/1Vx0L17hu9xMITa_lBBGcnWq39HbrFNOS?usp=drive_link <br>

## Data Cleaning and Creating the Win Feature
In the following cell, we separate the regular season from the testing data playoffs. We also drop records with missing values and games that ended in a tie. Lastly, we create the Win feature, which will act as the model target variable. <br>

```python
playoffs = df[df['season_type'] == 'POST']
df = df[df['season_type'] == 'REG']
df = df.dropna(subset=['posteam', 'down', 'score_differential', 'result'])
df = df[df['result'] != 0]

# result = home score - away score. Did the team with the ball end up winning? (1 = yes, 0 = no)
df['win'] = np.where(df['posteam_type'] == 'home', df['result'] > 0, df['result'] < 0).astype(int)
df[['game_id', 'posteam', 'score_differential', 'game_seconds_remaining', 'win']]
```

In the next cell, we choose what features we want to use for prediction; a list of them should be provided in the notebook in the cell above the one below:

```python
# setup variables
# Why can't we use result or the final score to predict win? (We only know the situation at that moment in the game)
X = df[[]]
y = df['win']
```

Next, we use train_test_split to randomly split our training and testing data. Why do we split by game and not by play?

```python
games = df['game_id'].unique()
train_games, test_games = train_test_split(games, test_size=0.2, random_state=42)

X_train, y_train = X[df['game_id'].isin(train_games)], y[df['game_id'].isin(train_games)]
X_test, y_test = X[df['game_id'].isin(test_games)], y[df['game_id'].isin(test_games)]
```

Now, we fit the XGBoost model, make predictions, and create a classification report. All of the parts are defined in the cell below. 

```python
# XGBoost = lots of small trees built one after another
# tree 1 makes a guess, tree 2 tries to fix tree 1's mistakes, tree 3 fixes what's left, ...
# n_estimators  = how many trees
# max_depth     = how big each tree is (keep them small)
# learning_rate = how much each new tree is allowed to change the prediction
model = XGBClassifier(n_estimators=100, max_depth=3, learning_rate=0.1, random_state=42)
model.fit(X_train, y_train)

y_pred = model.predict(X_test)

print("XGBoost Accuracy:", accuracy_score(y_test, y_pred))
print("\nClassification Report:\n ", classification_report(y_test, y_pred))
```

