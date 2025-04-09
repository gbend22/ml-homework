# House Prices - Advanced Regression Techniques

We start with a dataset which describes all types of houses and says what their sales price is.
With this data we need to build a model which accurately guesses what a house's price would be based on the data provided.

To solve this problem I tried multiple ways of dealing with Na variables, removing columns based on correlation and tried multiple other ways of processing the inputed data. After which I tried both Linear regression and Decision trees. The results of these experiments were rather shocking and I will share them to you below.

# Repository Structure

In this repository we see the Data folder which contains the train and test data tables.
I have 2 model_experiment .ipynb-s the first one is where I submit my work in mlflow, have the proper classes and pipelines. In the second one I conduct experiments to see what works or doesnt work and if the results are interesting or noteworthy I modify the first file and submit that run.

# Feature Engineering

First of all we need to deal with Na values. To do this I do the following:
1. Remove features that have more than 50% Na-s in them.
2. For the rest I fill them in with the most frequent value in the column(I tried to fill the numeric ones with the median but since the difference wasn't big for simplicity I simply left it like this).

Next, we need to deal with non-numeric values. For this i do the following:
1. For columns which have less than 5 unique values in them I use One Hot encoding.
2. For columns which hame more than 5 unique values in them I use Standard LabelEncoder.

# Feature Selection

In terms of feature selection I tried a few things to make the resulting model better. These include the following:
1. I tried using a correlation filter so that if 2 columns had a correlation more than 0.8(played with this number too) I dropped them. This method sadly didnt bring about the result I wanted and made the model a bit worse.
2. I tried using multiple scalers(Standard scaler, Minmax scaler) so that all of the features were in a certain range, but this didn't really improve the model that much(you can see this in mlflow)

# Training

For training I used 2 types of models Linear Regression and Decision trees. Between the two the Linear Regression did better, but the result from decision trees was interesting too(I forgot to set the max depth so it was way too overfitted, after realising that I found that having the max depth at 5 provided the most balanced result, meaning that the root mean square error of train and test were close enough).

In terms of hyperparameter testing I did quite a bit, as mentioned above I tested multiple depths for the decision tree, tried manipulating the threshold between owe and standard encoding of Na variables, the correlation barrier was also something to test which decided when 2 features were too correlated.

Even though I played around so much with so many different approaches to this problem for better or for worse I still found that the base model that I trained, the Linear regression with no correlation filters or scalers produced the best results. To compare different models I used 2 values, the root mean squared error and the r2 score. Both of them were a big help since with them I managed to find out if a model was overfitted/underfitted.

# MLflow Tracking

My MLflow experiments link is this: https://dagshub.com/gbend22/ml-homework.mlflow/

It is divided into 3 parts: testing(contains my first run), Linear_Regression(where I use linear regression with different scalers and hyperparameters) and Decision_Tree(where I use decision tree with different scalers and hyperparameters)

The metrics written in them are the r2 score and the root mean squared errors on train and test datasets. I store the Pipeline used to transform the inputed table and the trained model.

The best model's results were the following(It technically isn't the very best model but it is basically the same +-100 pm rmse and +-0.02 on r2):
1. Root Mean Squared Error (Train): 28511.80919690585
2. Root Mean Squared Error (Test): 33228.35741244413
3. R2 Score (Train): 0.863707536709239
4. R2 Score (Test): 0.8560525711025742
