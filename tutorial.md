# Sho's 20-min Python Pandas Tutorial

It is not uncommon to see a lot of people using Excel for data analysis. Excel is great, with a lot of in-built math and stats functions. Where is starts to fall apart is when you have a huge dataset (millions of record).

--

Think of Pandas as Python's Excel with even more flexibility. When you view Pandas DataFrames it looks like a spreadsheet or database table.
It supports various file formats OOB (csv, json, sql, html and more).

--

You can import from one format and export easily to another. Regardless of which data source you are dealing with, you get the same singular view using Pandas. It's great like that.
Let's get to it.

note:These instructions where written using python 3.
reference and credit: Thanks to [Sentdex](https://www.dataquest.io/blog/web-scraping-tutorial-python/) for the examples

Ready? To get started install Pandas

--

```bash
$ pip install pandas
```
---
# The basics
The standard way to import pandas is like below. Almost everyone assigns it a 'pd' alias once imported

```python
imports pandas as pd
```

DataFrames are at the core of pandas. You can reference elemts in a dataframe like you would a python dictionary.

--
For instance.

```python
data = {'temperature':[75, 73, 80, 64, 32], 'energy_reading':[11, 3, 14, 18, 24]}

df = pd.DataFrame(data) # creating a dataframe from the data
```
--



