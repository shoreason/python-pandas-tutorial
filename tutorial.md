# Sho's 20-min Python Pandas Tutorial

It is not uncommon to see a lot of people using Excel for data analysis. Excel is great, with a lot of in-built math and stats functions. Where is starts to fall apart is when you have a huge dataset (millions of record).

--

Think of Pandas as Python's Excel with even more flexibility. When you view Pandas DataFrames it looks like a spreadsheet or database table.
It supports various file formats OOB (csv, json, sql, html and more).

--

You can import from one format and export easily to another. Regardless of which data source you are dealing with, you get the same singular view using Pandas. It's great like that.
Let's get to it.

note:These instructions where written using python 3.
reference and credit: Thanks to [Sentdex](https://pythonprogramming.net/data-analysis-python-pandas-tutorial-introduction/) for the examples

Ready? To get started install Pandas

--

```bash
$ pip install pandas
```
---
# Getting Started
The standard way to import pandas is like below. Almost everyone assigns it a 'pd' alias once imported

```python
imports pandas as pd
```

DataFrames are at the core of pandas. You can reference elemts in a dataframe like you would a python dictionary.

--
For instance.

```python
data = {'temperature':[75, 73, 80, 64, 32, 65, 77], 'energy_reading':[11, 3, 14, 18, 24, 13, 6], 'day': [1, 2, 3, 4, 5, 6, 7]}

df = pd.DataFrame(data) # creating a dataframe from the data
```
--
Now we can preview the data by simply typing

```python
print(df)
```
That command prints out the dataset, but can be too much to see at once (especially with a lot of data). To preview the dataset you can just type any of the below

```python
print(df.head()) # shows you the top 5 rowa
print(df.tail()) # bottom 5 rows
print(df.tail(2)) # start from the bottom, but show me the last 2
```
---

# Filtering columns 

You can also just filter out rows you are interested in. If I wanted to print just the energy readings I could do this

```python
print(df.energy_reading) 
# or
print(df['energy_reading'])
# more than one column
print(df[['day', 'energy_reading']])
```
--

Sometimes the data we work with it is not scrubbed and could have missing value as 'NaN' which stands for 'Not a Number'. You easily replace such data using dataframes

```python
import numpy as np # to simulate a missing value

data_new = {'temperature':['75', '73', '80', '64', np.nan, '65', '77'],
'energy_reading':[np.nan, '3', '14', np.nan, '24', '13', '6'], 'day': [1, 2, 3, 4, 5, 6, 7]}

df_new = pd.DataFrame(data_new)
print(df_new.head())

#just replace the value those values with what you want
df_new = df_new.convert_objects(convert_numeric=True)
df_new.fillna(0, inplace=True)

print(df_new.head())
```
--

I can also choose to drop a column if I think it is no useful. Note: if you experimenting in your code you can try to retain the original dataframe and create a new one to drop columns off.

```python
original_df = pd.DataFrame.copy(df_new) # make copy of dataframe
df_new.drop(['energy_reading'], 1, inplace = True) # drop a energy reading

print(df_new.head())
print(original_df.head())
```
--

Lastly, let's try to filter a field based on a condition

```python
print(df_new[df_new.temperature > 70])
```

---
# Basic Math and stats

You can learn a lot from your data by simply using 'describe'

```python
print(df_new.describe())
```
You can get this data granually by doing

```python
df_new['temperature'].mean()
```
---

# Importing data 

This is a little straight forward

```python
df = pd.read_csv('your.csv') # to import csv
df = pd.read_json('your.json') # to import json
```

---

# Exercise

Now we can play with a lot more data. Import pandas_datareader module and use the code below to play with the dataset 

```python
import pandas as pd
import datetime
import pandas_datareader.data as web
import pandas_datareader as pdr

start = datetime.datetime(2010, 1, 1)
end = datetime.datetime(2015, 1, 1)

df = web.DataReader("XOM", "yahoo", start, end)

print(df.head())
```
--
[Learn More](https://www.youtube.com/watch?v=9d5-Ti6onew)





