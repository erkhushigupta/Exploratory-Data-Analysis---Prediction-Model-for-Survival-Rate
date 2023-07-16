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

### Some Predictions:
* Sex: Females are more likely to survive.
* SibSp/Parch: People traveling alone are more likely to survive.
* Age: Young children are more likely to survive.
* Pclass: People of higher socioeconomic class are more likely to survive.

   ## 4) Data Visualization
It's time to visualize our data so we can see whether our predictions were accurate! 

### Sex Feature
Percentage of females who survived: 74.20382165605095
Percentage of males who survived: 18.890814558058924
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/a9461388-5975-4074-8b3a-f9164570724b)
As predicted, females have a much higher chance of survival than males. The Sex feature is essential in our predictions.

### Pclass Feature
Percentage of Pclass = 1 who survived: 62.96296296296296
Percentage of Pclass = 2 who survived: 47.28260869565217
Percentage of Pclass = 3 who survived: 24.236252545824847
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/38a43e69-bafd-443e-9573-07e108dc77d6)
As predicted, people with higher socioeconomic class had a higher rate of survival. (62.9% vs. 47.3% vs. 24.2%)

### SibSp Feature
Percentage of SibSp = 0 who survived: 34.53947368421053
Percentage of SibSp = 1 who survived: 53.588516746411486
Percentage of SibSp = 2 who survived: 46.42857142857143
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/f4e61f53-0c6b-4733-974c-3c8d91d8d14f)

In general, it's clear that people with more siblings or spouses aboard were less likely to survive. However, contrary to expectations, people with no siblings or spouses were less to likely to survive than those with one or two. (34.5% vs 53.4% vs. 46.4%)

### Parch Feature
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/dac8d5e9-a9c0-49c9-a609-45568b3d06a0)

People with less than four parents or children aboard are more likely to survive than those with four or more. Again, people traveling alone are less likely to survive than those with 1-3 parents or children.

### Age Feature

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/cccd99d1-1801-41ad-9d00-cc7b3b3f7eaf)

Babies are more likely to survive than any other age group. 

### Cabin Feature
I think the idea here is that people with recorded cabin numbers are of higher socioeconomic class, and thus more likely to survive. 
Percentage of CabinBool = 1 who survived: 66.66666666666666
Percentage of CabinBool = 0 who survived: 29.985443959243085

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/8d8bb6f7-bf63-4094-a962-1c52f24d9931)

People with a recorded Cabin number are, in fact, more likely to survive. (66.6% vs 29.9%)

## 5) Cleaning Data
Time to clean our data to account for missing values and unnecessary information!
### Looking at the Test Data
Let's see how our test data looks!
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/40e18557-1b83-407c-ac51-ce49e2593ec7)
* We have a total of 418 passengers.
* 1 value from the Fare feature is missing.
* Around 20.5% of the Age feature is missing, we will need to fill that in.

### Cabin Feature
### Ticket Feature
### Embarked Feature

Number of people embarking in Southampton (S):
644
Number of people embarking in Cherbourg (C):
168
Number of people embarking in Queenstown (Q):
77
It's clear that the majority of people embarked in Southampton (S). Let's go ahead and fill in the missing values with S.

### Age Feature
Next we'll fill in the missing values in the Age feature. Since a higher percentage of values are missing, it would be illogical to fill all of them with the same value (as we did with Embarked). Instead, let's try to find a way to predict the missing ages. 

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/8d2e5972-cc80-4df0-ab99-d6cc49ffe7f7)

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/63c2ab15-675b-4303-a2d7-0ef75d92477b)

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/d8f8fb69-ec2c-47ce-bc8d-07ca2cc40ce4)

We'll try to predict the missing Age values from the most common age for their Title.
Now that we've filled in the missing values at least *somewhat* accurately (I will work on a better way for predicting missing age values), it's time to map each age group to a numerical value.

### Name Feature
We can drop the name feature now that we've extracted the titles.

### Sex Feature
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/9c48d691-ab8d-4c70-8f89-77ae8d0a4065)

### Embarked Feature

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/29e73f5f-b6ad-45b2-b22e-422dda96f997)

### Fare Feature
It's time separate the fare values into some logical groups as well as filling in the single missing value in the test dataset.

![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/074ac66a-315e-4036-8762-2a1dc78caa8f)
![image](https://github.com/erkhushigupta/Exploratory-Data-Analysis---Prediction-Model-for-Survival-Rate/assets/139675402/2d7a9934-0fd4-4854-ad48-cc48a94236ec)

## Sources:
* [Titanic Data Science Solutions](https://www.kaggle.com/startupsci/titanic-data-science-solutions)
* [Scikit-Learn ML from Start to Finish](https://www.kaggle.com/jeffd23/scikit-learn-ml-from-start-to-finish?scriptVersionId=320209)

 











