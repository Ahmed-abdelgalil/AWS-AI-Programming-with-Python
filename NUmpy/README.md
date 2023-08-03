# Numpy Notes 
### Why use Numpy?
1. Numpy is speed When performing operations on large arrays NumPy can often perform several orders of magnitude faster than Python lists. This speed comes from the nature of NumPy arrays being memory-efficient and from optimized algorithms used by NumPy for doing arithmetic, statistical, and linear algebra operations.
#### Example:
```
  import time
  import numpy as np
  x = np.random.random(100000000)
  
  # Case 1
  start = time.time()
  sum(x) / len(x)
  print(time.time() - start)
  
  # Case 2
  start = time.time()
  np.mean(x)
  print(time.time() - start)
```

### Creating and Saving NumPy ndarrays
-  a NumPy array is homogeneous, meaning all elements will have the same data-type
-   when we create an ndarray with both floats and integers, as we did with the z ndarray above, NumPy assigns its elements a float64 dtype as well.       This is called upcasting. Since all the elements of an ndarray must be of the same type
  #### Examples:
  ```
 ## We create a rank 1 ndarray that contains integers and floats
z = np.array([1, 2.5, 4])

print('The elements in z are of type:', z.dtype)

## output
## The elements in z are of type: float64

******************************************************

## We create a rank 1 ndarray from a Python list that contains integers and strings
x = np.array([1, 2, 'World'])

## We print information about x
print('x has dimensions:', x.shape)
print('The elements in x are of type:', x.dtype)

##output
x has dimensions: (3,)
The elements in x are of type: U21 ==> Unicode strings of 21 characters

******************************************************

Example 1.e - Using a 1-D Array of Float, and specifying the datatype of each element as int64

## We create a rank 1 ndarray of floats but set the dtype to int64
x = np.array([1.5, 2.2, 3.7, 4.0, 5.9], dtype = np.int64)
```
#### Save and Load Numpy array
```
## We create a rank 1 ndarray
x = np.array([1, 2, 3, 4, 5])

## We save x into the current directory as 
np.save('my_array', x)

y = np.load('my_array.npy')

```
