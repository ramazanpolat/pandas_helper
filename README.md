# **My Pandas DataFrame Cheat Sheet**

* DataFrame is like a table, consisting rows and column.
* DataFrame is a list of Series.
* Series is a list of values.
* Multiple series become a DataFrame.

## **Creating a DataFrame**

### Create from dict using one dict as one row (dict keys are used as column names):


```python
import pandas as pd
d = {'A': 11, 'B': 11}
df = pd.DataFrame.from_records([d])
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>11</td>
    </tr>
  </tbody>
</table>
</div>



### Create from dict using list of dicts (dict keys are used as column names):


```python
d1 = {'A': 11, 'B': 12}
d2 = {'A': 21, 'B': 22}
d3 = {'A': 31, 'B': 32}
d4 = {'A': 41, 'B': 42}
d5 = {'A': 51, 'B': 52}
d_list = [d1, d2, d3, d4, d5]
df = pd.DataFrame.from_records(d_list)
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



### Create from dict using one dict (keys as columns, values are rows for that column):


```python
dv = {
    'A': [11, 21, 31, 41, 51],
    'B': [12, 22, 32, 42, 52],
}
df = pd.DataFrame.from_dict(dv)
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



## **Column Operations**

### Get column names:


```python
df.columns
```




    Index(['A', 'B'], dtype='object')



### Get column names as list:


```python
list(df.columns)
```




    ['A', 'B']



### Get nth column name (n starts from 0):


```python
n = 0
df.columns[n]
```




    'A'



### Get one column **as Series**:


```python
df['A'] # or 
df.A
```




    0    11
    1    21
    2    31
    3    41
    4    51
    Name: A, dtype: int64



### Get one column **as DataFrame**:


```python
df[['A']]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
    </tr>
  </tbody>
</table>
</div>



### Get multiple columns **as DataFrame**:
Keep in mind that there is no way to get multiple columns as Series hence DataFrame itself is multiple Series.


```python
df[['A','B']]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



## **Row Operations**

### Get all rows:


```python
df # or
df[:]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



### Get slice of rows from 0 to 2 (includes 0, excludes 2):


```python
df[0:2]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
  </tbody>
</table>
</div>



### Get even rows from 0 to 4:
Using 2 steps gets you even rows


```python
df[0:4:2]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
  </tbody>
</table>
</div>



### Get all even rows:


```python
df[::2]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



### Get rows startin from 2:


```python
df[2:]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



### Get rows until 3(excluding 3):


```python
df[:3]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
  </tbody>
</table>
</div>



### Get all rows in reverse order:


```python
df[::-1]
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



## **Index**
* DataFrames have an index.
* Index is row number by default and starts with 0.
* Index can be defined while DataFrame created with 'index' parameter. If not provided, row numbers are used as index by default.
* Index is also a series if it consists only one column.
* Multiple column indexes are also supported.

### Default index:
Default index is row number which can be seen in output


```python
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>A</th>
      <th>B</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>11</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>22</td>
    </tr>
    <tr>
      <th>2</th>
      <td>31</td>
      <td>32</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41</td>
      <td>42</td>
    </tr>
    <tr>
      <th>4</th>
      <td>51</td>
      <td>52</td>
    </tr>
  </tbody>
</table>
</div>



Which is from 0 to 4 in the above example

## Getting index values:
Since it is the default index, it is a range index


```python
df.index
```




    RangeIndex(start=0, stop=5, step=1)



## Providing a column as index


```python
dv = {
    'i': [1, 2, 3, 4, 5],
    'A': [11, 21, 31, 41, 51],
    'B': [12, 22, 32, 42, 52],
}
df2 = pd.DataFrame.from_dict(dv).set_index('i')
df2
```

Here the `i` column become an index


```python
df2.index
```

As seen above, now the index is a list of integers (int64)

## Get index at location 3 (zero based)


```python
df2.index[3]
```

## Get the row where index is 3:


```python
df2.loc[3]
```


```python
df2
```

## Get the n-th row:


```python
n = 3
df2.iloc[n]
```


```python
# or 
df2[n:n+1]
```

The difference between **``df2.iloc[n]``** and **``df2[n:n+1]``** is, **``iloc``** always returns a **Series**, while the other returns a **DataFrame**.

# My Helpers
These helpers will make your life easy


```python
def df_col(self, column) -> pd.Series:
    if type(column) == int:
        return self[self.columns[column]].copy()
    if type(column) == str:
        return self[column].copy()
    raise ValueError(f"col parameter must be either type of 'str' or type of 'int' which '{column}' is not")


def df_cols(self, *columns) -> pd.DataFrame:
    cols_list = list(columns)
    new_cols_list = []
    for c in cols_list:
        if type(c) == int:
            new_cols_list.append(self.columns[c])
        else:
            new_cols_list.append(c)

    return self[new_cols_list].copy()


def df_row(self, ix) -> pd.Series:
    return self.iloc[ix]


def ser_col(self, column):
    return self.get(column)


def ser_cols(self, *columns):
    result = []
    for c in list(columns):
        result.append(self.get(c))

    return tuple(result)


pd.DataFrame.col = df_col
pd.DataFrame.cols = df_cols
pd.DataFrame.row = df_row
pd.DataFrame.rows = pd.DataFrame.iloc
pd.Series.col = pd.Series.get
pd.Series.cols = ser_cols
```

## Single Column Helper (col):
Returns **Series**


```python
df2.col(0) # Get first column as Series
df2.col('A') # Get column 'A' as Series
```

## Multiple Columns Helper (cols):
Returns **DataFrame**


```python
df2.cols(0,1) # Get column first and second as DataFrame
df2.cols('A', 'B') # Get column 'A' and 'B' as DataFrame
```

## Single Row Helper (row):
Returns **Series**


```python
df2.row(0) # Get first row as Series
```

## Multiple Rows Helper (rows):
Returns **DataFrame**


```python
df2.rows[0:3] # Get rows from 0 to 3 (excluding 3) as DataFrame
```

## Mixing Row and Column Helpers:

### Single column of single row -> raw value


```python
df2.row(0).col(0) # Get first column of first row as value
df2.row(0).col('A') # Get column 'A' of first row as value
```

### Multiple column of single row -> tuple:


```python
df2.row(0).cols(0, 1) # Get first two columns of first row as tuple
df2.row(0).cols('A', 'B') # Get 'A' and 'B' columns of first row as tuple
```

### Single column of multiple rows -> Series


```python
df2.rows[0:3].col(0) # Get first column of rows from 0 to 3 (excluding 3) as Series
df2.rows[0:3].col('A') # Get column 'A' of rows from 0 to 3 (excluding 3) as Series
```

### Multiple column of multiple rows -> DataFrame


```python
df2.rows[0:3].cols(0, 1) # Get first two column of rows from 0 to 3 (excluding 3) as DataFrame
df2.rows[0:3].cols('A', 'B') # Get 'A' and 'B' columns of rows from 0 to 3 (excluding 3) as DataFrame
```

### Single row of single column -> raw value:


```python
df2.col(0).row(0) # Get first row of first column as value
df2.col('A').row(0) # Get first row of column 'A' as value
```

### Multiple rows of single column -> numpy.ndarray:


```python
df2.col(0).rows[0:3] # Get rows from 0 to 3(excluding) of first column as numpy.ndarray
df2.col('A').rows[0:3] # Get rows from 0 to 3(excluding) of column 'A' as numpy.ndarray
```

### Single row of multiple columns -> Series:


```python
df2.cols(0, 1).row(0) # Get first row of first two columns as Series
df2.cols('A', 'B').row(0) # Get first row of columns 'A' and 'B' as Series
```

### Multiple rows of multiple columns -> DataFrame:


```python
df.cols(0, 1).rows[0:3] # Get rows from 0 to 3(excluding) of first two columns as DataFrame
df.cols('A', 'B').rows[0:3] # Get rows from 0 to 3(excluding) of of columns 'A' and 'B' as DataFrame
```
