# Jupyter Lab #

Experimenting with Jupyter and Pandas to see if it might be a helpful tool. It's a public repo because I want to be able to reference my own documentation from anywhere.

Install guide: https://jupyter.org/install

venv:
~~~console
python -m venv venv
venv/scripts/activate.ps1
~~~

Install:
~~~console
python -m pip install jupyterlab
~~~

Run:
~~~console
python -m jupyterlab
~~~

Panda docs:
* https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html#pandas.read_csv
* https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.head.html
* https://pandas.pydata.org/docs/reference/api/pandas.set_option.html
* https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.query.html

Example code:

Using example data from SMHI. Column index counting start at 0. The unnamed ;; row is named "Unnamed: 4" in the dataframe probably because it is column number 4.

~~~python
import pandas as pd
import os
~~~

Read from csv into a dataframe object (header sets which row to start to read from, starting from 0 and not counting empty lines):
~~~python
df = pd.read_csv(f'{os.getcwd()}\\smhi-opendata_1_64520_20221211_080324.csv', delimiter=';', header=7, dtype={'Unnamed: 4': 'string', 'Tidsutsnitt:': 'string'})
~~~

Show the types in the dataframe:
~~~python
df.dtypes
~~~

Allow unlimited or a set amount of rows to be displaying output (when setting a specific number, if output exceeds that value, the output will be truncated just like default):
~~~python
pd.set_option('display.max_rows', None)
pd.set_option('display.max_rows', 40)
~~~

Display the first rows (top to bottom) in the dataframe:
~~~python
df.head(100)
~~~

Display the last rows (bottom to top) in the dataframe:
~~~python
df.tail(100)
~~~

Filtering values can be done using 'query' (probably a lot more ways):
~~~python
df.query('Lufttemperatur < 1.0')
~~~