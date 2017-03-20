### Food Preferences of College Students

This dataset is a merged dataset from two previous datasets that include students' preferences in life, sports, food, GPA, height, weight
and other parameters, and a second dataset (taken from the exact same participants) entirely on food preferences of them and their parents. 

##### Libraries used

```python
import numpy
import pandas as pd as np
import matplotlib.pyplot as plt
import pyexcel as pe
```

#### Becoming familiar with the dataset
Once the dataset is uploaded we start getting an understanding of its shape. How many variables are in the dataset? How many cases have been collected?

``` python

food = pd.read_csv('food.csv')
cases = len(food)
print cases
food.shape
```

Then I turned every variable into a numerical variable if they had specific answer choices. One example of how to do that is the following:

``` python
food['parents_cook'] = food['parents_cook'].map({'Almost Everyday':1,'2-3 times a week':2, '1-2 times a week':3, 'On holidays only':4, 'Never':5})
```

