# XGBoost
XGBoost is a machine learning algorithm that uses a sequence of decision trees with weighted data to help improve prediction accuracy. 

## Today's Model
The model you will be making today uses data from the 2025 NFL season to predict a team's win chance throughout a game. <br>

**Open GitHub Desktop and then open the repo in VS Code (Make sure to pull any changes that have been made to the online repo).** <br>

At the top of the notebook, you will see the packages you will use and a preview of the table. Today, the CSV was too big to upload to GitHub, so download it from the link below. <br>

Link to CSV: https://drive.google.com/drive/folders/1Vx0L17hu9xMITa_lBBGcnWq39HbrFNOS?usp=drive_link <br>

## Data Cleaning and Creating the Win Feature
In the following cell, we separate the training data (regular season) from the testing data (playoffs). We also drop records with missing values and games that ended in a tie. Lastly, we create the Win feature, which will act as the model target variable. <br>

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
# Why can't we use result or the final score to predict win? (we only know the situation at that moment in the game)
X = df[[]]
y = df['win']
```
