# What is this?
This is an auto-contained example of a customized time-series split. It aims to solve the data-leakage problem that occurs when doing Cross Validation with a time-series dataset when your objective is to predict the next month.

### The problem

If you have two years of monthly data (ex: jan-2020 until dic-2021), you can define manually the lastest month as your test set and the other months as a whole as your train set. However, your train data (jan-2020 until nov-2021 included) will mix data from every month in each k-fold CV, unless we specify what rows will go in each k-fold CV. `sklearn.model_selection.TimeSeriesSplit()` assumes that each CV has the same number of rows, which not always is the case.

### The solution

I create a sample-dataset with different number of rows for each month, and a code sample for the CV-split according each month, with a `GridSearchCV()` code sample application on that split. It considers fixed and variable number of months to train.
