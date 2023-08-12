# Numpy Notes 
## Glossary 
**Below is the summary of all the functions and methods**
### Category: General Purpose
| Function/Method       | Description                                                                                               |
| --------------------- | --------------------------------------------------------------------------------------------------------- |
| `numpy.ndarray.dtype` | Return the data-type of the elements of the array. Remember, arrays are homogeneous.                      |
| `numpy.ndarray.ndim`  | Return the number of array-dimensions (rank), e.g., it will return 2 for a 4x3 array.                     |
| `numpy.ndarray.shape` | Return a tuple representing the array dimensions, e.g., it will return (rows,columns) for a rank 2 array. |
| `numpy.ndarray.size`  | Return the number of elements present in the array.                                                       |
| `numpy.save`          | Save an array to .npy (numpy) format.                                                                     |
| `numpy.load`          | Load array from the .npy files.                                                                           |
| `numpy.random.random` | Return random floats values from the interval [0.0, 1.0), in a specified shape.                          |
| `numpy.random.randint`| Return random integers from the half-open interval [a, b), in a specified shape.                          |
| `numpy.random.normal` | Return random samples from a Gaussian (normal) distribution.                                              |
| `numpy.random.permutation` | Return a randomly permuted sequence from the given list.                                             |
| `numpy.reshape`       | Reshape an array containing the same elements with a new shape, without affecting the original array.     |
| `numpy.ndarray.reshape`| Returns an array containing the same elements with a new shape, without affecting the original array.     |
### Category: Array Creation
  | Function/Method       | Description                                                                                               |
| --------------------- | --------------------------------------------------------------------------------------------------------- |
| `numpy.ones`          | Return a new array of given shape and type, filled with 1s.                                                |
| `numpy.zeros`         | Return a new array of given shape and type, filled with 0s.                                                |
| `numpy.full`          | Return a new array of given shape and type, filled with a specific value.                                  |
| `numpy.eye`           | Return a 2-D array with 1s on the diagonal and 0s elsewhere.                                               |
| `numpy.diag`          | Extract the diagonal elements.                                                                             |
| `numpy.unique`        | Return the sorted unique elements of an array.                                                             |
| `numpy.array`         | Create an n-dimensional array.                                                                             |
| `numpy.arange`        | Return evenly spaced values within a given half-open interval [a, b).                                      |
| `numpy.linspace`      | Return evenly spaced numbers over a specified interval [a,b].                                              |
| `numpy.ndarray.copy`  | Returns a copy of the array.                                                                               |
### Category: Operating with Elements and Indices
  | Function/Method             | Description                                                                                                                  |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `numpy.insert`              | Insert values along the given axis before the specified indices.                                                             |
| `numpy.delete`              | Return a new array, after deleting sub-arrays along a specified axis.                                                        |
| `numpy.append`              | Append values at the end of the specified array.                                                                             |
| `numpy.hstack`              | Return a stacked array formed by stacking the given arrays in sequence horizontally (column-wise).                            |
| `numpy.vstack`              | Return a stacked array formed by stacking the given arrays, will be at least 2-D, in sequence vertically (row-wise).         |
| `numpy.sort`                | Return a sorted copy of an array.                                                                                             |
| `numpy.ndarray.sort`        | Sort an array in-place.                                                                                                      |
### Category: Set Operations
  | Function/Method          | Description                                                                                                    |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| `numpy.intersect1d`      | Find the intersection of two arrays, i.e., the values common to both arrays.                                    |
| `numpy.setdiff1d`        | Find the set difference of two arrays, i.e., the values in the first array that are not present in the second. |
| `numpy.union1d`          | Return the unique, sorted array of values that are in either of the two input arrays.                          |
### Category: Arithmetic and Statistical Operations
  | Function/Method               | Description                                                                                       |
| ----------------------------- | ------------------------------------------------------------------------------------------------- |
| `numpy.add`                   | Element-wise addition of given arrays.                                                            |
| `numpy.subtract`              | Element-wise subtraction of arguments of given arrays.                                            |
| `numpy.multiply`              | Element-wise multiplication of arguments of given arrays.                                         |
| `numpy.divide`                | Element-wise division of the inputs.                                                              |
| `numpy.exp`                   | Calculate the exponential of all elements in the input array.                                     |
| `numpy.power`                 | Raise the first array elements to powers from the second array, element-wise.                     |
| `numpy.sqrt`                  | Return the non-negative square root of an array, element-wise.                                    |
| `numpy.ndarray.min`           | Return the minimum value along the specified axis.                                                |
| `numpy.ndarray.max`           | Return the maximum value along the specified axis.                                                |
| `numpy.mean`                  | Compute the arithmetic mean along the specified axis.                                             |
| `numpy.ndarray.mean`          | Compute the arithmetic mean along the specified axis for an ndarray.                              |
| `numpy.median`                | Compute the median along the specified axis.                                                      |

### Why use Numpy?
  1. Numpy is speed When performing operations on large arrays NumPy can often perform several orders of magnitude faster than Python lists. This speed comes from the nature of NumPy arrays being     memory-efficient and from optimized algorithms used by NumPy for doing arithmetic, statistical, and linear algebra operations.
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
  -   when we create an ndarray with both floats and integers, as we did with the z ndarray above, NumPy assigns its elements a float64 dtype as well.       This is called upcasting. Since all         the elements of an ndarray must be of the same type
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
  
  # We print the elements above the main diagonal of X
  print('y =', np.diag(X, k=1))
  
  # We print the elements below the main diagonal of X
  print('w = ', np.diag(X, k=-1))
  
  # We create a 1000 x 1000 ndarray of random floats drawn from normal (Gaussian) distribution
  # with a mean of zero and a standard deviation of 0.1.
  X = np.random.normal(0, 0.1, size=(1000,1000))
  ```
  - numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0)
  - additional resource ==> https://numpy.org/devdocs/user/basics.creation.html#array-creation

### Accessing, Deleting, and Inserting slicing Elements Into ndarrays
  - Accessing and modify 1-d elements array like normal array
  - To Accessing and modify 2-d elements array ==> X[0,0] - which is first row and first column
  - Delete elements
    ```
    # We delete the first and fifth element of x
    x = np.delete(x, [0,4])
  
    # We delete the first row of y
    w = np.delete(Y, 0, axis=0)
  
     # We delete the first and third column of y
    v = np.delete(Y, [0,2], axis=1)
    ```
  - Append elements
    ```
    # We append the integer 7 and 8 to x
    x = np.append(x, [7,8])
    
    # We append a new row containing 7,8,9 to y
    v = np.append(Y, [[7,8,9]], axis=0)
    
    # We append a new column containing 9 and 10 to y
    q = np.append(Y,[[9],[10]], axis=1)
    ```
  - Insert elements --> This function inserts the given list of elements to ndarray right before the given index along the specified axis
    ```
    # We insert the integer 3 and 4 before index 2 in x.
    x = np.insert(x,2,[3,4])
    
    # We insert a row between the first and second row of y
    w = np.insert(Y,1,[4,5,6],axis=0)
    
    # We insert a column full of 5s between the first and second column of y
    v = np.insert(Y,1,5, axis=1)
    
    ```
  - numpy.hstack and numpy.vstack
    ```
    # We stack x on top of Y
    z = np.vstack((x,Y)) ==> z =
                                [[1 2] --> x
                                [3 4]
                                [5 6]]
    
    # We stack x on the right of Y. We need to reshape x in order to stack it on the right of Y. 
    w = np.hstack((Y,x.reshape(2,1))) ==> w =
                                            [[3 4 1]
                                            [5 6 2]]
  
        
    ```
### Slicing in a 2-D ndarray, Boolean Indexing, Set Operations, and Sorting
  - slicing 
  ```
    X =
      [[ 0 1 2 3 4]
      [ 5 6 7 8 9]
      [10 11 12 13 14]
      [15 16 17 18 19]]
  
    # We select all the elements that are in the 2nd through 4th rows and in the 3rd to 5th columns
    Z = X[1:4,2:5] ==> [[ 7 8 9]
                        [12 13 14]
                        [17 18 19]]
  
    
    
  ```
  - numpy.unique --> numpy.unique(array, return_index=False, return_inverse=False, return_counts=False, axis=None)
  - Boolean indexing
  ```
  # We use Boolean indexing to assign the elements that are between 10 and 17 the value of -1
  X[(X > 10) & (X < 17)] = -1
  ```
  - set operations
  ```
  # We use set operations to compare x and y:
  print('The elements that are both in x and y:', np.intersect1d(x,y))
  print('The elements that are in x that are not in y:', np.setdiff1d(x,y))
  print('All the elements of x and y:',np.union1d(x,y))
  ```
  - numpy.sort function --> numpy.sort(array, axis=-1, kind=None, order=None)
### Arithmetic operations and Broadcasting
  - Element-wise arithmetic operations on 1-D arrays
    ```
    # We perform basic element-wise operations using arithmetic symbols and functions
    print( X + Y)
    print('add(X,Y) = \n', np.add(X,Y))
    print(X - Y)
    print('subtract(X,Y) = \n', np.subtract(X,Y))
    print( X*  Y)
    print('multiply(X,Y) = \n', np.multiply(X,Y))
    print( X / Y)
    print('divide(X,Y) = \n', np.divide(X,Y))
    ```
  -  Additional mathematical functions (broadcasting)

    ```
      # We apply different mathematical functions to all elements of x
      print('EXP(x) =', np.exp(x))
      print('SQRT(x) =',np.sqrt(x))
      print('POW(x,2) =',np.power(x,2)) # We raise all elements to the power of 2
    ```
  - Statistical functions
      - X.mean()
      -  X.sum()
      -  X.std()
      -  np.median(X)
      -  X.max()
      -  X.min()
  - NOTE:
      -  NumPy is able to add 1 x 3 and 3 x 1 ndarrays to 3 x 3 ndarrays by broadcasting the smaller ndarrays along the big ndarray so that they have compatible shapes
   
