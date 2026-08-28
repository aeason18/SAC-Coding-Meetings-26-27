# Lesson 3: Classification
There are many different kinds of classification models; today you will learn about **Logistic Regression.**

## What is Logistic Regression?
Logistic Regression models use multiple independent variables to predict the value of a dependent discrete variable (strike/ball, run/pass). <br> 

## Today's Model
The model you will be making today uses NFL QB data from 2016 to 2025. At the end, you will have a model that tells you which 2025 QB looked the most like past MVPs. <br>

**Open GitHub Desktop and then open the repo in VS Code.** <br>

You will notice your imports cell and the cell that reads in the CSV. <br>

After that, you have your VIF values. Do you remember what the VIF values tell you about your data? <br>

## Training VS Testing Data
In this cell is where you start to separate your training data from your testing data. You must never test on data that you trained on, so for example, if you wanted to predict for the year 2022 and you have data from 2016-2025, only train your model on data from 2016-2021. Here, you can see that you designate 2016-2024 as your testing years. <br>

```python
features = []

X = train[features]
y = train['MVP']
X = X.astype(float)

X = sm.add_constant(X) 
model = sm.Logit(y, X).fit()
print(model.summary())
```

Now, if you pressed Run All, you will get an error in this cell. This will be because your model has no X values to read from, and you need to choose some features for your model to use. <br>

## Model Output
After doing that, you should have a model output. You do not evaluate logistic regression models using the model output like you do for linear regression. The output gives you a Pseudo R-squared value, but it doesn't hold as much meaning as it does for linear regression. This model output tells you if your features are statistically significant and how important they are. Evaluation strategies will be discussed more later. <br>

## Results and Model Evaluation
Once you get to the cell where you run your predictions, it should make you a nice plot to display who your model believes played the most like past MVPs. Does your model agree that Matt Stafford should have won MVP in 2025? <br>

Below that, you will have a plot that displays your model's ROC curve. It should look something like this: <br>

![ROC_SAC.png](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/ROC_SAC.png)

What this graph is saying is that to identify 100% of real MVPs, the model had to label 20-25% of Non-MVPs as MVPs. It appears that most of that labeling happened after it had correctly identified 80% of the real MVPs. This tells you that your model performed really well! <br>

There were two years where the model I made was wrong (features used were: 'aggressiveness', 'db_epa', 'TO', 'Wins', 'tot_TD') one of which was a close between Aaron Rodgers and Tom Brady in 2021, and the other was 2023, where it predicted Dak Prescott to win but had very low values for everyone so I wanted to look at why. (Lamar Jackson was the actual winner)<br>

Here is a plot that can help break this down: <br>





