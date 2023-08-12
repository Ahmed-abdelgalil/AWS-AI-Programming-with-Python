# Pandas Notes
***Pandas*** is a package for data manipulation and analysis in Python. The name Pandas is derived from the econometrics term Panel Data. Pandas incorporates two additional data structures into Python, namely Pandas Series and Pandas DataFrame. These data structures allow us to work with labeled and relational data in an easy and intuitive manner
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


