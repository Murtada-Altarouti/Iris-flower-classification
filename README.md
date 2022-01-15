# Iris Flower Classification 🌸

## Table of Content 📕
* [1. Project Overview](#project_overview)
* [2. Problem Statement](#problem_statement)
* [3. Metrics](#metrics)
* [4. The Iris Flower Dataset](#the_iris_flower_dataset)
    * [A. Dataset Source](#dataset_source)
    * [B. Data Exploration and Data Visualization](#data_exploration_and_data_visualization)
* [5. Methodology](#methodology)
   * [A. Data Preprocessing](#data_preprocessing)
   * [B. Implementation](#implementation)
   * [C. Refinement](#refinement)
* [6. Results](#results)
   * [Model Evaluation and Validation](#evaluation)
   * [Justification](#justification)
* [7. Flask Web App](#flask_web_app)
* [8. Files Structure](#files_structure)
* [9. Requirments](#requirments)
* [10. Running Process](#running_process)
    * [A. Process Data](#process_data)
    * [B. Training the classifier](#training_the_classifier)
    * [C. Run the Flask Web App](#run_the_flask_web_app)
* [11. Conclusion](#conclusion)
* [12. Acknowledgements](#acknowledgements)

***
<a id=project_overview></a>
## 1. Project Overview 💡
In this project, we will analyze the iris flower dataset, which has three species: Setosa, Versicolor and Virginica. Each flower class has around 50 records in the dataset. The main goal of this project is to create a classification model that uses the length and width measurements of the sepal and petal to categorize new flowers.

![image](https://github.com/Murtada-Altarouti/Iris-flower-classification/blob/main/images/flower.jpg)

<a id=problem_statement></a>
## 2. Problem Statement 📌
Identifying Iris Flowers by eyes and especially for non-experts is a difficult job, but machine learning algorithms make it much easier to classify any flower with high accuracy. This is a classification problem which the model attempts to determine if the flower was Setosa, Versicolor, or Virginica. In this project, we are going to use [Logistic Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) from the scikit-learn library.

<a id=metrics></a>
## 3. Metrics 🧮
In the evaluation process, we are going to use the accuracy score metrics to get an overview on the model performance, which is the number of correctly classified data instances over the total number of data instances.

![image](https://github.com/Murtada-Altarouti/Iris-flower-classification/blob/main/images/formula.png)

<a id=the_iris_flower_dataset></a>
## 4. The Iris Flower Dataset 🌸

<a id=dataset_source></a>
### A. Dataset Source 📋
The Iris flower dataset was taken from [Kaggle](https://www.kaggle.com/arshid/iris-flower-dataset) as a comma-separated values (CSV), and it contains a set of 150 records under 5 attributes - Petal Length, Petal Width, Sepal Length, Sepal width and Class(Species).

<a id=data_exploration_and_data_visualization></a>
### B. Data Exploration and Data Visualization 🔎
The data exploration and data visualization were done inside the `/data/process_data.ipynb`, but here are some of the findings:

![image](https://github.com/Murtada-Altarouti/Iris-flower-classification/blob/main/images/dataset.png)

As seen above, there are almost 50 records of each flower class in the dataset

![image](https://github.com/Murtada-Altarouti/Iris-flower-classification/blob/main/images/values.png)

As it shown above, the sepal range is between 4.3cm and 7.9cm in length and 2.0cm and 4.4cm in width. But the petal range is between 1.0cm and 6.9cm in length and 0.1cm and 2.5cm in width.

The chart also shows that Virginica has the longest sepal length which may reach 7.9cm, as opposed to Setosa, which has a range of 4.3cm to 5.8cm. On the other hand, Setosa has the widest sepals at 4.4cm and Virginica has the highest petal length and width.

<a id=Methodology></a>
## 5. Methodology 📜
The machine learning model was trained on the Iris flower dataset using The [scikit learn](https://scikit-learn.org/stable/) Python library. The model is [Logistic Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html), which is an excellent classifier since it applies the one-vs-rest principle to this multi-class situation. We also used the [accuracy score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html) metrics to calculate the model accuracy. 

<a id=data_preprocessing></a>
### A. Data Preprocessing 🗃️
The data preprocessing was done inside the `/data/process_data.ipynb` using Pandas library. There was only one step which is encoding the classes from strings to numbers since computers deal with numbers better than anything.

<a id=implementation></a>
### B. Implementation 📋
The implementation of algorthims and techniques was done by using the [scikit-learn](https://scikit-learn.org/) library. This procedure consists of five phases, which are as follows: 
   i. Loading the data as a pandas dataframe from the database
   ii. Spliting the dataset to train and test using [train test split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html) function
   iii. building and training the logistic regression model
   iv. Evaluating the model using the [accuracy score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html?highlight=accuracy%20score#sklearn.metrics.accuracy_score)
   v. Saving the model as a pickle file 

<a id=refinement></a>
### C. refinement 📡
In this project, GridSearchCV was used which is an exhaustve search over specified parameter values for an estimator. The following are the hyperparameters that was given to the grid search:
```python
 parameters = {
     'C': [0.1, 1, 10, 100],
     'penalty': ['l1', 'l2', 'elasticnet'],
     'solver': ['lbfgs', 'liblinear'],
     'max_iter': [100, 500]
 }
```

<a id=results></a>
## 6. Results 🏁

<a id=evaluation></a>
### A. Model Evaluation and Validation 🪄
The model evaluation was calculated using the [accuracy score](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.accuracy_score.html?highlight=accuracy%20score#sklearn.metrics.accuracy_score) and the GridSearchCV identified the following as the optimal hyperparameters for which the model achieved a 96% accuracy score.
```python
Best parameters: {'C': 10, 'max_iter': 100, 'penalty': 'l2', 'solver': 'lbfgs'}
```

<a id=justification></a>
### B. Justification 🖊️
In this project, the grid search was the only strategy used, and we received a high accuracy with the best parameters.

<a id=flask_web_app></a>
## 7. Flask Web App 🌐
The Flask Web App allows the user to use the trained model to make predictions on new flowers and find their species easily
![image](https://github.com/Murtada-Altarouti/Iris-flower-classification/blob/main/images/webapp.png)

<a id=files_structure></a>
## 8. Files Structure 📁
```
├── app #Website folder
│   ├── app.py #Responsible of running the website
│   └── templates
│       ├── index.html # Allows the user to input and predict new flower properties 
│   └── Static 
│       ├── index.css # This file has the Cascading Style Sheets of the index.html
|
├── data
│   ├── dataset.csv # The Iris flower dataset
│   ├── dataset.db #The prepared dataset as SQLite database
│   └── process_data.py #Responsible for dataset preparation
|
├── models
│   ├── model.pkl #The Logistic Regression Model
│   └── train_classifier.py #Responsible for creating the machine learning model
|
├── images #This folder contains all images for the readme file
│   ├── flower.jpg
|
└── README.md #Readme file 
```

<a id=requirments></a>
## 9. Requirments 📑
In order to to run this project, you must have [Python3](https://www.python.org/) installed on your machine. You also must have all listed libraries inside the `requirments.txt` so run the following command to install them: 
```
pip3 install -r requirments.txt
```
<a id=running_process></a>
## 10. Running Process ⏯️
This secions explains how to run each part of this project using the command prompt or terminal

<a id=process_data></a>
### A. Process Data 🔨
To look at the data exploration and data visualization, please open `/data/process_data.ipynb` with [Jupyter Notebook](https://jupyter.org/).

<a id=training_the_classifier></a>
### B. Training the classifier ⚙️
To re-train the classifier, you must go inside the `models` directory using the terminal or the command prompt and run the following:
```shell
python3 train_classifier.py ../data/<database_name>.db <model_name>.pkl
```
<a id=run_the_flask_web_app></a>
### C. Run the Flask Web App 🌐
To run the web app, you must go inside the `app` directory using the terminal or the command prompt and run the following:
```shell
python3 app.py
```
The link of the website will be `0.0.0.0:3001`

<a id=conclusion></a>
## 11. Conclusion 👋
We conclude that it may be difficult for non-experts to identify iris flower species, machine learning makes it much easier to find out the flower class with 96% accuracy. In the future, we can try to develop a deep learning model utilizing neural networks, which may yield even better and more accurate results. Also, feel free to fork this repositry and try to improve the solution. 

<a id=acknowledgements></a>
## 12. Acknowledgements ❤️
I would like to express my appreciation to [Misk Academy](https://misk.org.sa/en/) and [Udacity](https://www.udacity.com/) for the amazing work on the data science course and the support they give us to build this project
