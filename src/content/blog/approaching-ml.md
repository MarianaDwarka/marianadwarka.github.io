---
title: "How to Approach Machine Learning Projects"
description: "The machine learning process starts with understanding the problem and classifying the model type. Next, the data is cleaned, explored, and split into training and test sets, followed by training a baseline model. Finally, advanced strategies are experimented with, hyperparameters are tuned, and results are interpreted to improve predictions."
pubDate: "Oct 30 2023"
heroImage: "/blogImages/approach.png"
---

We'll explore a step-by-step process for approaching ML problems:

1. Understand the business requirements and the nature of the available data.
2. Classify the problem as supervised/unsupervised and regression/classification.
3. Download, clean & explore the data and create new features that may improve models.
4. Create training/test/validation sets and prepare the data for training ML models.
5. Create a quick & easy baseline model to evaluate and benchmark future models.
6. Pick a modeling strategy, train a model, and tune hyperparameters to achieve optimal fit.
7. Experiment and combine results from multiple strategies to get a better result.
8. Interpret models, study individual predictions, and present your findings. 


## Step 1 - Understand Business Requirements & Nature of Data

Most machine learning models are trained to serve a real-world use case. It's important to understand the business requirements, modeling objectives and the nature of the data available before you start building a machine learning model.

### Understanding the Big Picture

The first step in any machine learning problem is to read the given documentation, talk to various stakeholders and identify the following:

1. What is the business problem you're trying to solve using machine learning?
2. Why are we interested in solving this problem? What impact will it have on the business?
3. How is this problem solved currently, without any machine learning tools?
4. Who will use the results of this model, and how does it fit into other business processes?
5. How much historical data do we have, and how was it collected?
6. What features does the historical data contain? Does it contain the historical values for what we're trying to predict.
7. What are some known issues with the data (data entry errors, missing data, differences in units etc.)
8. Can we look at some sample rows from the dataset? How representative are they of the entire dataset.
9. Where is the data stored and how will you get access to it?
10. ...


Gather as much information about the problem as possible, so that you're clear understanding of the objective and feasibility of the project.

## Step 2 - Classify the problem as supervised/unsupervised & regression/classification

Once you understand the problem, classify it into the right category:

Supervised learning: You have input-output pairs (labeled data). This could be a classification (e.g., binary, multiclass) or regression (predicting continuous values).
Unsupervised learning: You work with data that has no labels, typically for clustering, anomaly detection, or association tasks.

Here are more information ([source](https://vas3k.com/blog/machine_learning/)): 

<img src="https://i.imgur.com/VbVFAsg.png">

### Loss Functions and Evaluation Metrics

Once you have identified the type of problem you're solving, you need to pick an appropriate evaluation metric. Also, depending on the kind of model you train, your model will also use a loss/cost function to optimize during the training process.

* **Evaluation metrics** - they're used by humans to evaluate the ML model

* **Loss functions** - they're used by computers to optimize the ML model

They are often the same (e.g. RMSE for regression problems), but they can be different (e.g. Cross entropy and Accuracy for classification problems).

## Step 3 - Download, clean & explore the data and create new features

Data is rarely clean, so this step is essential for success. It involves:

* Handling missing or inconsistent data (e.g., imputation).
* Removing outliers or irrelevant data.
* Performing exploratory data analysis (EDA): Visualizing distributions, relationships between variables, and understanding the dataset.
* Creating new features (feature engineering) that might improve the model’s predictive power.


### Downloading Data

There may be different sources to get the data:

* CSV files
* SQL databases
* Raw File URLs
* Kaggle datasets 
* Google Drive
* Dropbox
* etc.

Identify the right tool/library to get the data. 

### Cleaning Data

Cleaning the data is an essential part of preparing your dataset for analysis or machine learning models. Here are the key steps involved in cleaning the data:

* Handling Missing Data
* Dealing with Outliers
* Correcting Data Types
* Handling Duplicates
* Standardizing or Normalizing Data
* Encoding Categorical Variables
* Dealing with Inconsistent Data
* Feature Scaling


### Exploratory Data Analysis and Visualization

Objectives of exploratory data analysis:

- Study the distributions of individual columns (uniform, normal, exponential)
- Detect anomalies or errors in the data (e.g. missing/incorrect values)
- Study the relationship of target column with other columns (linear, non-linear etc.)
- Gather insights about the problem and the dataset
- Come up with ideas for preprocessing and feature engineering

### Feature Engineering

Feature engineer is the process of creating new features (columns) by transforming/combining existing features or by incorporating data from external sources. 


For example, here are some features that can be extracted from the "Date" column:

1. Day of week
2. Day or month
3. Month
4. Year
5. Weekend/Weekday
6. Month/Quarter

## Step 4 - Create a training/test/validation split and prepare the data for training

You need to split the data into different sets:

* **Training set:** Used to train the model.
* **Validation set:** Used for tuning model hyperparameters and model selection.
* **Test set:** Used for the final evaluation of the model’s performance.
It's also important to preprocess the data (e.g., normalization, standardization, encoding categorical variables) to make it ready for machine learning algorithms.

## Step 5 - Create quick & easy baseline models to benchmark future models

Before diving into complex models, start with a simple baseline model to set a performance benchmark. This could be a basic algorithm like a decision tree, logistic regression, or even a rule-based model. It gives you a reference point to see if more sophisticated models actually improve performance.

A quick baseline model helps establish the minimum score any ML model you train should achieve.

### Baseline ML model

Let's train a simple `LinearRegression` model, with no customization.

`model.fit` uses the following workflow for training the model ([source](https://www.deepnetts.com/blog/from-basic-machine-learning-to-deep-learning-in-5-minutes.html)):

1. We initialize a model with random parameters (weights & biases).
2. We pass some inputs into the model to obtain predictions.
3. We compare the model's predictions with the actual targets using the loss function.  
4. We use an optimization technique (like least squares, gradient descent etc.) to reduce the loss by adjusting the weights & biases of the model
5. We repeat steps 1 to 4 till the predictions from the model are good enough.


<img src="https://www.deepnetts.com/blog/wp-content/uploads/2019/02/SupervisedLearning.png" width="480">

Once we have fit the model, the model can now be used to make predictions. Note that the parameters of the model will not be updated during prediction.

## Step 6 - Pick a strategy, train a model & tune hyperparameters


Choose the type of model(s) that suit your problem. It could be decision trees, random forests, support vector machines, neural networks, etc. Train your model and adjust hyperparameters (e.g., learning rate, regularization strength) to improve performance using the validation set.

### Systematically Exploring Modeling Strategies

Scikit-learn offers the following cheatsheet to decide which model to pick.

![](https://scikit-learn.org/1.5/_downloads/b82bf6cd7438a351f19fac60fbc0d927/ml_map.svg)


Here's the general strategy to follow:

- Find out which models are applicable to the problem you're solving.
- Train a basic version for each type of model that's applicable
- Identify the modeling approaches that work well and tune their hypeparameters
- [Use a spreadsheet](https://docs.google.com/spreadsheets/d/1S42lnklqdj4hS3BohffyvZVJOFBZJ61VDiHLMuf2zBw/edit?usp=sharing) to keep track of your experiments and results.

## Step 7 - Experiment and combine results from multiple strategies

In general, the following strategies can be used to improve the performance of a model:

- Gather more data. A greater amount of data can let you learn more relationships and generalize the model better.
- Include more features. The more relevant the features for predicting the target, the better the model gets.
- Tune the hyperparameters of the model. Increase the capacity of the model while ensuring that it doesn't overfit.
- Look at the specific examples where the model make incorrect or bad predictions and gather some insights
- Try strategies like grid search for hyperparameter optimization and K-fold cross validation
- Combine results from different types of models (ensembling), or train another model using their results.

### Hyperparameter Optimization & Grid Search

You can tune hyperparameters manually, our use an automated tuning strategy like random search or Grid search. Follow this tutorial for hyperparameter tuning using Grid search: https://machinelearningmastery.com/hyperparameter-optimization-with-random-search-and-grid-search/

<img src="https://i.imgur.com/EJCrSZw.png" width="480">

## Step 8 - Interpret models, study individual predictions & present your findings

Interpreting the model is critical, especially in business settings where decision-makers need to trust the model. You should:

Look at feature importance to understand which features are driving the predictions.
Analyze individual predictions and ensure the model is making reasonable decisions.
Present your results in a way that is understandable for non-technical stakeholders (e.g., visualizations, actionable insights).

### Feature Importance

You'll need to explain why your model returns a particular result. Most scikit-learn models offer some kind of "feature importance" score.

### Presenting your results

* Create a presentation for non-technical stakeholders
* Understand your audience - figure out what they care about most
* Avoid showing any code or technical jargon, include visualizations
* Focus on metrics that are relevant for the business
* Talk about feature importance and how to interpret results
* Explain the strengths and limitations of the model
* Explain how the model can be improved over time

### Model Deployment

At this point, the model can be handed over to a software developer / ML engineer who can put the model into production, as part of an existing software system. It's important to monitor the results of the model, and make improvements from time to time.

Check out this tutorial on how to deploy a model to the Heroku platform using the Flask framework: https://towardsdatascience.com/create-an-api-to-deploy-machine-learning-models-using-flask-and-heroku-67a011800c50


## Summary and References


Here's the summary of the step-by-step process you should follow to approach any machine learning problem:

1. Understand the business requirements and the nature of the available data.
2. Classify the problem as supervised/unsupervised and regression/classification.
3. Download, clean & explore the data and create new features that may improve models.
4. Create training/test/validation sets and prepare the data for training ML models.
5. Create a quick & easy baseline model to evaluate and benchmark future models.
5. Pick a modeling strategy, train a model, and tune hyperparameters to achieve optimal fit.
6. Experiment and combine results from multiple strategies to get a better overall result.
7. Interpret models, study individual predictions, and present your findings. 
