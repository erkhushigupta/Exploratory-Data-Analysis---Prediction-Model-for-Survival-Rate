# Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate


Building a prediction model to predict the survival rate of a class of people using passenger data. The training data included name, gender, economic status, passenger class, fare, cabin , age with data size of 891 with ground truth training records and 419 records for testing purposes.

### Contents:
1. Import Necessary Libraries
2. Read In and Explore the Data
3. Data Analysis
4. Data Visualization
5. Cleaning Data

## 1) Import Necessary Libraries
First off, we need to import several Python libraries such as numpy, pandas, matplotlib and seaborn.

This code block imports necessary data analysis and visualization libraries for Python:

    numpy (abbreviated as np) is a library for numerical computing with Python. It provides powerful tools for working with arrays and matrices, as well as various mathematical functions.
    pandas (abbreviated as pd) is a library for data manipulation and analysis in Python. It provides data structures for efficiently storing and analyzing data, such as data frames and series.
    matplotlib.pyplot (abbreviated as plt) is a plotting library for Python that provides a variety of visualizations, including line charts, scatter plots, histograms, and more.
    seaborn is a data visualization library based on matplotlib. It provides a higher-level interface for creating statistical graphics.
    %matplotlib inline is a magic command for Jupyter notebooks that enables displaying of plots inline within the notebook.

The last code block warnings.filterwarnings('ignore') is used to suppress warning messages in the output.

## 2) Read in and Explore the Data 
It's time to read in our training and testing data using `pd.read_csv`, and take a first look at the training data using the `describe()` function.

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/d14d3eb0-dded-4281-aaf3-d9d9078bb318)



