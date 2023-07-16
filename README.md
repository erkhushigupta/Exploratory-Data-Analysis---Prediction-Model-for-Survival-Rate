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

## 3) Data Analysis
We're going to consider the features in the dataset and how complete they are. 

Index(['PassengerId', 'Survived', 'Pclass', 'Name', 'Sex', 'Age', 'SibSp',
       'Parch', 'Ticket', 'Fare', 'Cabin', 'Embarked'],
      dtype='object')
      
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/3e1100ec-8188-4c20-a454-0352fcdb49ac)

* **Numerical Features:** Age (Continuous), Fare (Continuous), SibSp (Discrete), Parch (Discrete)
* **Categorical Features:** Survived, Sex, Embarked, Pclass
* **Alphanumeric Features:** Ticket, Cabin

#### What are the data types for each feature?
* Survived: int
* Pclass: int
* Name: string
* Sex: string
* Age: float
* SibSp: int
* Parch: int
* Ticket: string
* Fare: float
* Cabin: string
* Embarked: string

Now that we have an idea of what kinds of features we're working with, we can see how much information we have about each of them.
#### Some Observations:
* There are a total of 891 passengers in our training set.
* The Age feature is missing approximately 19.8% of its values. I'm guessing that the Age feature is pretty important to survival, so we should probably attempt to fill these gaps. 
* The Cabin feature is missing approximately 77.1% of its values. Since so much of the feature is missing, it would be hard to fill in the missing values. We'll probably drop these values from our dataset.
* The Embarked feature is missing 0.22% of its values, which should be relatively harmless.

PassengerId      0
Survived         0
Pclass           0
Name             0
Sex              0
Age            177
SibSp            0
Parch            0
Ticket           0
Fare             0
Cabin          687
Embarked         2
dtype: int64
