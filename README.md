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
y = dataset.iloc[:, -1].values # Matrix of features of independent variable
```
