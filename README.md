# Machine Learning In Python

This git page provides a simple readme with some documentation and tips regarding machine learning in Python.
The intended use of this page was to serve as a personal refernce sheet when developing machine learning models using Python, 
but I have decided to share with whoever else might find these resources useful. Contained within the repository :
- Guides :
    1. data_preprocessing
    2. regression
        1. Simple Linear Regression
        2. Multiple Linear Regression
        3. Polynomial Linear Regression
- Templates
    - data_preprocessing templates
    - data_preprocessing tools

Finally, all the resources found in this repository have been compiled from the [Machine Learning A-Z™: Hands-On Python & R In Data Science](https://www.udemy.com/course/machinelearning/ "Machine Learning A-Z") course by  Kirill Eremenko, Hadelin de Ponteves, SuperDataScience Team, SuperDataScience Support. I do not credit for any of the code written here and simply aim to use this as a foundation when developing code for my own application.

# Numpy
Allows you to work with arrays and do mathametical operations
```python
import numpy as np
```

# Matplotlib
Allows you to build chart
```python
import matplotlib.pyplot as plt
```

**Scatter plot with regression line**:
```python
plt.scatter(X_train, y_train,color='red')
plt.plot(X_train,regressor.predict(X_train),color='blue')
plt.title('Salary vs Experience')
plt.xlabel('Years of Experience')
plt.ylabel('Salary (R)')
plt.show()
```

**Set decimal points**:
```python
np.set_printoptions(precision=2)
```

**Set concatenate**:
```python
np.concatenate()
```

**Reshape**:
```python
array.reshape(columns, rows)
```

# Panda 
Allows you to import a dataset and easily create vectors and matrices
```python
import pandas as pd
```

**Importing a Dataset:**
```python
dataset = pd.read_csv('Data.csv')
# iloc[rows,columns] is used to reference local indexes
X = dataset.iloc[:, :-1].values # Matrix of features. Note that range includes lower bound but does not include upper bound of '-1'
y = dataset.iloc[:, -1].values # Matrix of features of dependent variable
```

# scikit-learn

**impute**
SimpleImputer
```python
from sklearn.impute import SimpleImputer
# SimpleImputer(missing_values,strategy)
imputer = SimpleImputer(missing_values=np.nan, strategy='mean') # Replace the missing value with the mean of the feature itself
imputer.fit(X[:,1:3])   # Only expects columns with numerical values
X[:,1:3] = imputer.transform(X[:,1:3])     # Performs transformation and replaces missing data with numeric mean, and returns the new data. Be sure only to change the affected 
```

**compose**
```python
from sklearn.compose import ColumnTransformer
# ColumnTransformer(
#     transformers=[(typeOfTransformation,NameOfTheClassForTheTransformation,[columnsToApplyTo])],
#     remainder = what to do with columns with no transformation
#     )
ct = ColumnTransformer(transformers=[('encoder',OneHotEncoder(),[0])],remainder='passthrough') # 'passthrough' leaves columns as is
X = np.array(ct.fit_transform(X)) # Fit and transform the data in one step, force output to numpy array
```

**preprocessing**
```python
from sklearn.preprocessing import OneHotEncoder # Module for One Hot Encoding

from sklearn.preprocessing import LabelEncoder # Module for Label Encoding
le =LabelEncoder()
y = le.fit_transform(y) # No need for this to be numpy array

from sklearn.preprocessing import StandardScaler # Module for standardisation feature scaling
sc = StandardScaler()
X = sc.fit_transform(X) # Keeps X as a numpy array

from sklearn.preprocessing import PolynomialFeatures # Transformer module
sc = StandardScaler()
poly_reg = PolynomialFeatures(degree=2)
X_poly = poly_reg.fit_transform(X) # Tool to transfer matrix of features X to X_poly by adding additional polynomial terms
```

**model_selection**
```python
from sklearn.model_selection import train_test_split


import sklearn.model_selection import train_test_split # Module for splitting training data and test data, this is a function import
# train_test_split(X matrix,y matrix,test_size= percentage of data to be in test set, random_state=0 (Optional) )
# return :  [X_train, X_test, Y_train, Y_test]
```

**linear_model**
```python
from sklearn.linear_model import LinearRegression # Linear Regression Model
regressor = LinearRegression() 
regressor.fit(X_train,y_train) # trains simple and multiple Linear Regression Model
y_pred = regressor.predict(X_test) # uses model to make a prediction
```


