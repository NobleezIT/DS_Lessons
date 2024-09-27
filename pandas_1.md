# What is Pandas?
Pandas is a popular open-source data manipulation and analysis library for the Python programming language. It provides a powerful and flexible set of tools for working with structured data, making it a fundamental tool for data scientists, analysts, and engineers.
Pandas is designed to handle data in various formats, such as tabular data, time series data, and more, making it an essential part of the data processing workflow in many industries.

## Here are some key features and functionalities of Pandas:

**Data Structures:** Pandas offers two primary data structures - DataFrame and Series.

A **DataFrame** is a two-dimensional, size-mutable, and potentially heterogeneous tabular data structure with labeled axes (rows and columns).

A **Series** is a one-dimensional labeled array, essentially a single column or row of data.

**Data Import and Export:** Pandas makes it easy to read data from various sources, including CSV files, Excel spreadsheets, SQL databases, and more. It can also export data to these formats, enabling seamless data exchange.

**Data Merging and Joining:** You can combine multiple DataFrames using methods like merge and join, similar to SQL operations, to create more complex datasets from different sources.

**Efficient Indexing:** Pandas provides efficient indexing and selection methods, allowing you to access specific rows and columns of data quickly.

**Custom Data Structures:** You can create custom data structures and manipulate data in ways that suit your specific needs, extending Pandas' capabilities.

## Importing Pandas:
Import Pandas using the import command, followed by the library's name.
Commonly, Pandas is imported as pd for brevity in code.


```python
conda install pandas
pip install pandas
```


```python
import pandas as pd
```


```python
file.pdf, file.html, file.json, file.csv, file.tsv, tab seperated values, file.xlsx, file.txt, 
```

Data Loading:

Pandas can be used to load data from various sources, such as CSV and Excel files.

The read_csv function is used to load data from a CSV file into a Pandas DataFrame.

To read a CSV (Comma-Separated Values) file in Python using the Pandas library, you can use the pd.read_csv() function. Here's the syntax to read a CSV file:


```python
import pandas as pd

# Read the CSV file into a DataFrame
df = pd.read_csv('your_file.csv')
```


    ---------------------------------------------------------------------------

    FileNotFoundError                         Traceback (most recent call last)

    Cell In[2], line 4
          1 import pandas as pd
          3 # Read the CSV file into a DataFrame
    ----> 4 df = pd.read_csv('your_file.csv')
    

    File ~\miniconda3\Lib\site-packages\pandas\io\parsers\readers.py:1026, in read_csv(filepath_or_buffer, sep, delimiter, header, names, index_col, usecols, dtype, engine, converters, true_values, false_values, skipinitialspace, skiprows, skipfooter, nrows, na_values, keep_default_na, na_filter, verbose, skip_blank_lines, parse_dates, infer_datetime_format, keep_date_col, date_parser, date_format, dayfirst, cache_dates, iterator, chunksize, compression, thousands, decimal, lineterminator, quotechar, quoting, doublequote, escapechar, comment, encoding, encoding_errors, dialect, on_bad_lines, delim_whitespace, low_memory, memory_map, float_precision, storage_options, dtype_backend)
       1013 kwds_defaults = _refine_defaults_read(
       1014     dialect,
       1015     delimiter,
       (...)
       1022     dtype_backend=dtype_backend,
       1023 )
       1024 kwds.update(kwds_defaults)
    -> 1026 return _read(filepath_or_buffer, kwds)
    

    File ~\miniconda3\Lib\site-packages\pandas\io\parsers\readers.py:620, in _read(filepath_or_buffer, kwds)
        617 _validate_names(kwds.get("names", None))
        619 # Create the parser.
    --> 620 parser = TextFileReader(filepath_or_buffer, **kwds)
        622 if chunksize or iterator:
        623     return parser
    

    File ~\miniconda3\Lib\site-packages\pandas\io\parsers\readers.py:1620, in TextFileReader.__init__(self, f, engine, **kwds)
       1617     self.options["has_index_names"] = kwds["has_index_names"]
       1619 self.handles: IOHandles | None = None
    -> 1620 self._engine = self._make_engine(f, self.engine)
    

    File ~\miniconda3\Lib\site-packages\pandas\io\parsers\readers.py:1880, in TextFileReader._make_engine(self, f, engine)
       1878     if "b" not in mode:
       1879         mode += "b"
    -> 1880 self.handles = get_handle(
       1881     f,
       1882     mode,
       1883     encoding=self.options.get("encoding", None),
       1884     compression=self.options.get("compression", None),
       1885     memory_map=self.options.get("memory_map", False),
       1886     is_text=is_text,
       1887     errors=self.options.get("encoding_errors", "strict"),
       1888     storage_options=self.options.get("storage_options", None),
       1889 )
       1890 assert self.handles is not None
       1891 f = self.handles.handle
    

    File ~\miniconda3\Lib\site-packages\pandas\io\common.py:873, in get_handle(path_or_buf, mode, encoding, compression, memory_map, is_text, errors, storage_options)
        868 elif isinstance(handle, str):
        869     # Check whether the filename is to be opened in binary mode.
        870     # Binary mode does not support 'encoding' and 'newline'.
        871     if ioargs.encoding and "b" not in ioargs.mode:
        872         # Encoding
    --> 873         handle = open(
        874             handle,
        875             ioargs.mode,
        876             encoding=ioargs.encoding,
        877             errors=errors,
        878             newline="",
        879         )
        880     else:
        881         # Binary mode
        882         handle = open(handle, ioargs.mode)
    

    FileNotFoundError: [Errno 2] No such file or directory: 'your_file.csv'


### What is a Series?
A Series is a one-dimensional labeled array in Pandas. It can be thought of as a single column of data with labels or indices for each element. You can create a Series from various data sources, such as lists, NumPy arrays, or dictionaries

Here's a basic example of creating a Series in Pandas:


```python
import pandas as pd

# Create a Series from a list
mylist = [10, 20, 30, 40, 50]
s = pd.Series(mylist)

print(s)
```

    0    10
    1    20
    2    30
    3    40
    4    50
    dtype: int64
    


```python
# Create a Series from a list
mylist2 = [10, 20, 30, 40, 50]
ds = pd.Series(mylist2, index = ['A', 'B', 'C', 'D', 'E']) # Specifying index with a label
ds
```




    A    10
    B    20
    C    30
    D    40
    E    50
    dtype: int64



### Accessing Elements in a Series
You can access elements in a Series using the index labels or integer positions. Here are a few common methods for accessing Series data:


```python
x = pd.Series([12, 24, 32, 48])
x
```




    0    12
    1    24
    2    32
    3    48
    dtype: int64




```python
mylist[2]
```




    30




```python
mylist[2:4]
```




    [30, 40]




```python
print(s[2])
```

    30
    


```python
print(x[0])
```

    12
    


```python
print(s[2])     # Access the element with label 2 (value 30)
```

    30
    

Accessing by position


```python
print(s.iloc[3]) # Access the element at position 3 (value 40)
```

    40
    


```python
print(s.iloc[0])
```

    10
    

Accessing multiple elements


```python
print(s[1:4])   # Access a range of elements by label
```

    1    20
    2    30
    3    40
    dtype: int64
    


```python
print(x[2:3])
```

    2    32
    dtype: int64
    


```python
ds.index
```




    Index(['A', 'B', 'C', 'D', 'E'], dtype='object')




```python
ds.values
```




    array([10, 20, 30, 40, 50], dtype=int64)




```python
ds.shape
```




    (5,)




```python
ds.sum()
```




    150



### Series Attributes and Methods
Pandas Series come with various attributes and methods to help you manipulate and analyze data effectively. Here are a few essential ones:

- values: Returns the Series data as a NumPy array.

- index: Returns the index (labels) of the Series.

- shape: Returns a tuple representing the dimensions of the Series.

- size: Returns the number of elements in the Series.

- mean(), sum(), min(), max(): Calculate summary statistics of the data.

- unique(), nunique(): Get unique values or the number of unique values.

- sort_values(), sort_index(): Sort the Series by values or index labels.

- isnull(), notnull(): Check for missing (NaN) or non-missing values.

- apply(): Apply a custom function to each element of the Series.


```python
s.values
```




    array([10, 20, 30, 40, 50])



## What is a DataFrames?
A DataFrame is a two-dimensional labeled data structure with columns of potentially different data types. Think of it as a table where each column represents a variable, and each row represents an observation or data point. DataFrames are suitable for a wide range of data, including structured data from CSV files, Excel spreadsheets, SQL databases, and more.

### Creating DataFrames from Dictionaries:
DataFrames can be created from dictionaries, with keys as column labels and values as lists representing rows.


```python
record = {'Name': "Abdul", 'Id': 2345}
record

```




    {'Name': 'Abdul', 'Id': 2345}




```python
import pandas as pd

# Creating a DataFrame from a dictionary
data = {'Name': ['Alice', 'Bob', 'Charlie', 'David'],
        'Age': [25, 30, 35, 28],
        'City': ['New York', 'San Francisco', 'Los Angeles', 'Chicago']}

print(data)
df = pd.DataFrame(data, index = ['A', 'B', 'C', 'D'])

print(df)

```

    {'Name': ['Alice', 'Bob', 'Charlie', 'David'], 'Age': [25, 30, 35, 28], 'City': ['New York', 'San Francisco', 'Los Angeles', 'Chicago']}
          Name  Age           City
    A    Alice   25       New York
    B      Bob   30  San Francisco
    C  Charlie   35    Los Angeles
    D    David   28        Chicago
    

### Column Selection:
You can select a single column from a DataFrame by specifying the column name within double brackets.
Multiple columns can be selected in a similar manner, creating a new DataFrame.


```python
print(df['Name'])  # Access the 'Name' column
print(type(df['Name']))
```

    0      Alice
    1        Bob
    2    Charlie
    3      David
    Name: Name, dtype: object
    <class 'pandas.core.series.Series'>
    


```python
print(df[['Name']])
print(type(df[['Name']]))
```

          Name
    0    Alice
    1      Bob
    2  Charlie
    3    David
    <class 'pandas.core.frame.DataFrame'>
    


```python

```


```python
print(df[['Name', 'Age']])
```

          Name  Age
    0    Alice   25
    1      Bob   30
    2  Charlie   35
    3    David   28
    

### Accessing Rows:
You can access rows by their index using .iloc[] or by label using .loc[].


```python
print(df.iloc[0])   # Access the third row by position
#    # Access the second row by label
```

    Name       Alice
    Age           25
    City    New York
    Name: 0, dtype: object
    


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>Alice</td>
      <td>25</td>
      <td>New York</td>
    </tr>
    <tr>
      <th>B</th>
      <td>Bob</td>
      <td>30</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>C</th>
      <td>Charlie</td>
      <td>35</td>
      <td>Los Angeles</td>
    </tr>
    <tr>
      <th>D</th>
      <td>David</td>
      <td>28</td>
      <td>Chicago</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[0]
```




    Name       Alice
    Age           25
    City    New York
    Name: A, dtype: object




```python
print(df.loc['A'])
print(df.loc['C'])
```

    Name       Alice
    Age           25
    City    New York
    Name: A, dtype: object
    Name        Charlie
    Age              35
    City    Los Angeles
    Name: C, dtype: object
    

### Slicing:
You can slice DataFrames to select specific rows and columns.


```python
print(df[['Name', 'Age']])  # Select specific columns
print(df[1:3])             # Select specific rows
df2 = df[['Name', 'Age']]
```

          Name  Age
    A    Alice   25
    B      Bob   30
    C  Charlie   35
    D    David   28
          Name  Age           City
    B      Bob   30  San Francisco
    C  Charlie   35    Los Angeles
    


```python
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>A</th>
      <td>Alice</td>
      <td>25</td>
    </tr>
    <tr>
      <th>B</th>
      <td>Bob</td>
      <td>30</td>
    </tr>
    <tr>
      <th>C</th>
      <td>Charlie</td>
      <td>35</td>
    </tr>
    <tr>
      <th>D</th>
      <td>David</td>
      <td>28</td>
    </tr>
  </tbody>
</table>
</div>




```python
df3 = df[1:3]
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>B</th>
      <td>Bob</td>
      <td>30</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>C</th>
      <td>Charlie</td>
      <td>35</td>
      <td>Los Angeles</td>
    </tr>
  </tbody>
</table>
</div>



### Finding Unique Elements:
Use the unique method to determine the unique elements in a column of a DataFrame.


```python
unique_dates = df['Age'].unique()
unique_dates
```




    array([25, 30, 35, 28], dtype=int64)




```python
df[df["Age"] > 25]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>B</th>
      <td>Bob</td>
      <td>30</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>C</th>
      <td>Charlie</td>
      <td>35</td>
      <td>Los Angeles</td>
    </tr>
    <tr>
      <th>D</th>
      <td>David</td>
      <td>28</td>
      <td>Chicago</td>
    </tr>
  </tbody>
</table>
</div>



### Conditional Filtering:
You can filter data in a DataFrame based on conditions using inequality operators.
For instance, you can filter albums released after a certain year.


```python
high_above = df[df['Age'] > 25]
high_above
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>City</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>B</th>
      <td>Bob</td>
      <td>30</td>
      <td>San Francisco</td>
    </tr>
    <tr>
      <th>C</th>
      <td>Charlie</td>
      <td>35</td>
      <td>Los Angeles</td>
    </tr>
    <tr>
      <th>D</th>
      <td>David</td>
      <td>28</td>
      <td>Chicago</td>
    </tr>
  </tbody>
</table>
</div>



### Saving DataFrames:
To save a DataFrame to a CSV file, use the to_csv method and specify the filename with a “.csv” extension.Pandas provides other functions for saving DataFrames in different formats.


```python
df.to_csv('trading_data.csv', index=False)
```

## DataFrame Attributes and Methods
DataFrames provide numerous attributes and methods for data manipulation and analysis, including:

shape: Returns the dimensions (number of rows and columns) of the DataFrame.

info(): Provides a summary of the DataFrame, including data types and non-null counts.

describe(): Generates summary statistics for numerical columns.

head(), tail(): Displays the first or last n rows of the DataFrame.

mean(), sum(), min(), max(): Calculate summary statistics for columns.

sort_values(): Sort the DataFrame by one or more columns.

groupby(): Group data based on specific columns for aggregation.

fillna(), drop(), rename(): Handle missing values, drop columns, or rename columns.

apply(): Apply a function to each element, row, or column of the DataFrame.

# Conclusion
In conclusion, mastering the use of Pandas Series and DataFrames is essential for effective data manipulation and analysis in Python. Series provide a foundation for handling one-dimensional data with labels, while DataFrames offer a versatile, table-like structure for working with two-dimensional data. Whether you're cleaning, exploring, transforming, or analyzing data, these Pandas data structures, along with their attributes and methods, empower you to efficiently and flexibly manipulate data to derive valuable insights. By incorporating Series and DataFrames into your data science toolkit, you'll be well-prepared to tackle a wide range of data-related tasks and enhance your data analysis capabilities.
To further your skills in data analysis with Pandas, consider the following next steps:
