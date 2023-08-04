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

### Using Built-in Functions to Create ndarrays

#### Examples:

```
# We create a 2 x 3 ndarray full of fives. 
X = np.full((2,3), 5) ==> The np.full() function creates by default an array with the same data type as the constant value used to fill in the array.

# We create a 5 x 5 Identity matrix (diagonal is 1's and other is 0's). 
X = np.eye(5)

# Create a 4 x 4 diagonal matrix that contains the numbers 10,20,30, and 50
# on its main diagonal
X = np.diag([10,20,30,50])

# We create a 1000 x 1000 ndarray of random floats drawn from normal (Gaussian) distribution
# with a mean of zero and a standard deviation of 0.1.
X = np.random.normal(0, 0.1, size=(1000,1000))
```
- numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0)
- additional resource ==> https://numpy.org/devdocs/user/basics.creation.html#array-creation
