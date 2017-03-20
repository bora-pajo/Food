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
Cleaning continued by dropping all the blanks and missing values
```python
df=food
df_no_missing = df.dropna()
df_no_missing.head(2)
```
and for cleaning the cases that are entirely blank
```python
df_cleaned = df.dropna(how='all')
```
finally adding 0 instead of NaN
```python
df=df.fillna(0)
```
Then I wanted to save the file into a clean csv file to save it for later work on it. To do so
```python
import pyexcel as pe
sheet = pyexcel.get_sheet(adict=food1)
sheet.save_as("output.csv")
```



