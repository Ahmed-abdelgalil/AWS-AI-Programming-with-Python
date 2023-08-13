# Pandas Notes
***Pandas*** is a package for data manipulation and analysis in Python. The name Pandas is derived from the econometrics term Panel Data. Pandas incorporates two additional data structures into Python, namely Pandas Series and Pandas DataFrame. These data structures allow us to work with labeled and relational data in an easy and intuitive manner
## Glossary
*Below is the summary of all the functions and methods that you learned in this lesson:*
### Category: Initialization and Utility
| Function/Method                        | Description                                                                               |
|----------------------------------------|-------------------------------------------------------------------------------------------|
| `pandas.read_csv(relative_path_to_file)`  | Reads a CSV file at `relative_path_to_file` and loads it as a DataFrame.                 |
| `pandas.DataFrame(data)`                | Returns a 2-D heterogeneous tabular data.                                                 |
| `pandas.Series(data, index)`            | Returns a 1-D ndarray with axis labels.                                                  |
| `pandas.Series.shape`                   | Returns a tuple representing the dimensions.                                             |
| `pandas.DataFrame.shape`                | Returns a tuple representing the dimensions.                                             |
| `pandas.Series.ndim`                    | Returns the number of dimensions.                                                        |
| `pandas.DataFrame.ndim`                 | Returns the number of dimensions (rank).                                                 |
| `pandas.Series.size`                    | Returns the number of elements.                                                          |
| `pandas.DataFrame.size`                 | Returns the number of elements.                                                          |
| `pandas.Series.values`                  | Returns the data available in the Series.                                                |
| `pandas.Series.index`                   | Returns the indexes available in the Series.                                             |
| `pandas.DataFrame.isnull()`             | Returns a same-sized object with True for NaN elements and False otherwise.              |
| `pandas.DataFrame.count(axis)`          | Returns the count of non-NaN values along the given axis.                                |
| `pandas.DataFrame.head([n])`           | Returns the first `n` rows from the DataFrame (default `n=5`).                            |
| `pandas.DataFrame.tail([n])`           | Returns the last `n` rows from the DataFrame (default `n=5`). Supports negative indexing. |
| `pandas.DataFrame.describe()`           | Generates descriptive statistics (count, mean, std deviation, min, max).                  |
| `pandas.DataFrame.min()`                | Returns the minimum of the values along the given axis.                                   |
| `pandas.DataFrame.max()`                | Returns the maximum of the values along the given axis.                                   |
| `pandas.DataFrame.mean()`               | Returns the mean of the values along the given axis.                                      |
| `pandas.DataFrame.corr()`               | Computes pairwise correlation of columns, excluding NA/null values.                       |
| `pandas.DataFrame.rolling(windows)`     | Provides rolling window calculation, e.g., `.rolling(15).mean()` for window size of 15.   |
| `pandas.DataFrame.loc[label]`           | Accesses a group of rows and columns by label(s).                                         |
| `pandas.DataFrame.groupby(mapping_function)` | Groups the DataFrame using a given mapper function or Series of columns.                   |

### Category: Manipulation
| Function/Method                                   | Description                                                                                                           |
|---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
| `pandas.Series.drop(index)`                       | Drops the element positioned at the given index(es).                                                                |
| `pandas.DataFrame.drop(labels)`                   | Drops specified labels (entire columns or rows) from the dataframe.                                                 |
| `pandas.DataFrame.pop(item)`                      | Returns the item and drops it from the DataFrame. If not found, raises a KeyError.                                  |
| `pandas.DataFrame.insert(location, column, values)` | Inserts a column with the given values into the DataFrame at the specified location.                              |
| `pandas.DataFrame.rename(dictionary-like)`         | Renames label(s) (columns or row-indexes) as mentioned in the dictionary-like.                                     |
| `pandas.DataFrame.set_index(keys)`                | Sets the DataFrame's row-indexes using existing column-values.                                                      |
| `pandas.DataFrame.dropna(axis)`                   | Removes rows (if axis=0) or columns (if axis=1) that contain missing values.                                       |
| `pandas.DataFrame.fillna(value, method, axis)`    | Replaces NaN values with the specified value along the given axis, using the given method (`backfill`, `bfill`, `pad`, `ffill`, `None`). |
| `pandas.DataFrame.interpolate(method, axis)`      | Replaces the NaN values with estimated values calculated using the given method along the given axis.             |

## Why Use pandas?
Pandas Series and DataFrames are designed for fast data analysis and manipulation, as well as being flexible and easy to use. Below are just a few features that makes Pandas an excellent package for data analysis:

- Allows the use of labels for rows and columns
- Can calculate rolling statistics on time series data
- Easy handling of NaN values
- Is able to load data of different formats into DataFrames
- Can join and merge different datasets together
- It integrates with NumPy and Matplotlib

## Pandas Series ([Documnetation](https://pandas.pydata.org/pandas-docs/stable/reference/series.html))
A Pandas series is a one-dimensional array-like object that can hold many data types, such as numbers or strings, and has an option to provide axis labels
### Difference between NumPy ndarrays and Pandas Series
1. One of the main differences between Pandas Series and NumPy ndarrays is that you can assign an index label to each element in the Pandas Series. In other words, you can name the indices of your Pandas Series anything you want.
2. Another big difference between Pandas Series and NumPy ndarrays is that Pandas Series can hold data of different data types.
#### Example 1 - Create a Series
  ```
  # We import Pandas as pd into Python
  import pandas as pd
  
  # We create a Pandas Series that stores a grocery list
  groceries = pd.Series(data = [30, 6, 'Yes', 'No'], index = ['eggs', 'apples', 'milk', 'bread'])
  
  # We display the Groceries Pandas Series
  groceries
  eggs           30
  apples         6
  milk         Yes
  bread       No
  dtype: object
  ```
### Accessing and Deleting Elements in pandas Series
#### Example 1. Access, Mutate elements using index labels
  ```  
  # we can access single or multiple index labels
  print(groceries[['milk', 'bread']], groceries['eggs']) 
  
  # we use loc to access multiple index labels
  print(groceries.loc[['eggs', 'apples']]) 
  
  # We access elements in Groceries using numerical indices:
  
  # we use multiple numerical indices
  print(groceries[[0, 1]])

  
  # We use a single numerical index
  print('How many eggs do we need to buy:', groceries[0]) 
  print()
  # we use iloc to access multiple numerical indices
  print('Do we need milk and bread:\n', groceries.iloc[[2, 3]])

  # We change the number of eggs to 2
  groceries['eggs'] = 2

  ```
#### Example 2. Delete elements using drop()
```
  # We remove apples from our grocery list. The drop function removes elements out of place don't delete from original series
  print('We remove apples (out of place):\n', groceries.drop('apples'))

  # We remove apples from our grocery list in place by setting the inplace keyword to True delete from orginal list
  groceries.drop('apples', inplace = True)
```
### Arithmetic Operations on pandas Series
- Just like with NumPy ndarrays, we can perform element-wise arithmetic operations on Pandas Series.
- We can Use mathematical functions from NumPy to operate on Series like:
    - np.exp(fruits))
    - np.sqrt(fruits)
    - np.power(fruits,2) # We raise all elements of fruits to the power of 2
- Perform arithmetic operations on selected elements
#### Example 4. Perform multiplication on a Series having integer and string elements
```
  # We multiply our grocery list by 2
  groceries * 2
--------------------------
  eggs                 60
  apples             12
  milk         YesYes
  bread        NoNo
  dtype: object
```
- Note: We can't divide / in example above so we want to make sure that arithmetic operations are valid on* all* the data types of your elements.


