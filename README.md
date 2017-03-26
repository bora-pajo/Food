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

#### Additional information on the variables

*1) Approximately how many days a week did your parents cook?*

1 - Almost everyday
2 - 2-3 times a week
3 - 1-2 times a week
4 - on holidays only
5 - never

*3) was your favorite food cooked at home or store bought?*

1 - cooked at home
2 - store bought
3 - both bought at store and cooked at home

*4) How likely to teat fruit in a day*

1 - very unlikely
2 - unlikely
3 - neutral
4 - likely
5 - very likely

*5) - How likely to eat veggies in a day*

1 - very unlikely
2 - unlikely
3 - neutral
4 - likely
5 - very likely

*6) drink, fries, soup, breakfast*

1 - Option 1
2 - Option 2

*7) How likely to eat ethnic food, thai food, indian food, italian food, persian food, greek food*

1 - very unlikely
2 - unlikely
3 - neutral
4 - likely
5 - very likely

*8) Vitamins*

1 - Yes
2 - No

*9) checking nutritional values*

1 - never
2 - on certain products only
3 - very rarely
4 - on most products
5 - on everything

*10) importance of consuming calories per day*

1 - i dont know how many calories i should consume
2 - it is not at all important
3 - it is moderately important
4 - it is very important

*11) Guessing calories in a scone*

1 - 107 cal
2 - 315 cal
3 - 420 cal
4 - 980 cal


*12) guessing calories in chicken piadina*

1 - 265
2 - 430
3 - 610
4 - 720

*13) guessing calories in turkey sandwhich*

1 - 345
2 - 500
3 - 690
4 - 850

*14) guessing calories in waffle potato sandwhich*

1 - 575
2 - 760
3 - 900
4 - 1315

*15) guessing calories in a tortilla sandwhich*

1 - 580
2 - 725
3 - 940
4 - 1165

*16) self perception of weight*

6 - i dont think myself in these terms
5 - overweight
4 - slightly overweight
3 - just right
2 - very fit
1 - slim

*17) gender*

1 - female
2 - male

*18) grade level*

1 - freshman
2 -Sophomore
3 - Junior
4 - Senior

*19) marital status*

1 -Single
2 - In a relationship
3 - Cohabiting
4 - Married
5 - Divorced
6 - Widowed

*20) mother and father's education*

1 - less than high school
2 - high school degree
3 - some college degree
4 - college degree
5 - graduate degree

*21) income*

1 - less than $15,000
2 - $15,001 to $30,000
3 - $30,001 to $50,000
4 - $50,001 to $70,000
5 - $70,001 to $100,000
6 - higher than $100,000

*22) living*

1 - On campus
2 - Rent out of campus
3 - Live with my parents and commute
4 - Own my own house

*23) employment*

1 - yes full time
2 - yes part time
3 - no

*24) Cook*

1 - Every day
2 - A couple of times a week
3 - Whenever I can, but that is not very often 
4 - I only help a little during holidays
5 - Never, I really do not know my way around a kitchen

*25) How much would you pay for meal out*

1 - up to $5.00
2 - $5.01 to $10.00
3 - $10.01 to $20.00
4 - $20.01 to $30.00
5 - $30.01 to $40.00
6 - more than $40.01

*26) frequency of eating out in a week*

1 - Never
2 - 1-2 times
3 - 2-3 times
4 - 3-5 times
5 - every day

*27) find life rewarding and feel very healthy*

1 to 10 where 1 is strongly agree and 10 is strongly disagree - scale


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
sheet = pyexcel.get_sheet(adict=food)
sheet.save_as("output.csv")
```


