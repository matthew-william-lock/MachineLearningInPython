# Machine Learning In Python
This provides a simple readme with some documentation and tips regarding machine learning in Python.

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
from sklearn.preprocessing import OneHotEncoder # Module for One Hot Encoding
```

**preprocessing**
```python
from sklearn.compose import ColumnTransformer
# ColumnTransformer(
#     transformers=[(typeOfTransformation,NameOfTheClassForTheTransformation,[columnsToApplyTo])],
#     remainder = what to do with columns with no transformation
#     )
ct = ColumnTransformer(transformers=[('encoder',OneHotEncoder,[0])],remainder='passthrough') # 'passthrough' leaves columns as is
```


**model_selection**
```python
from sklearn.model_selection import train_test_split
```

