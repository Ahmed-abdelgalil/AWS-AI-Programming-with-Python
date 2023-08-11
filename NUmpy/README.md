# Numpy Notes 
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
   
### Category: General Purpose
  ![image](https://github.com/Ahmed-abdelgalil/AWS-AI-Programming-with-Python/assets/103966424/2c2375a7-e892-4e18-9b8d-4940ac93f3ee)
### Category: Array Creation
  ![image](https://github.com/Ahmed-abdelgalil/AWS-AI-Programming-with-Python/assets/103966424/d33c3fc5-74fe-4911-bee8-66e60531b6a2)
### Category: Operating with Elements and Indices
  ![image](https://github.com/Ahmed-abdelgalil/AWS-AI-Programming-with-Python/assets/103966424/17dbbcab-9e1d-4d4b-b845-0fd474d0a45a)
### Category: Set Operations
![image](https://github.com/Ahmed-abdelgalil/AWS-AI-Programming-with-Python/assets/103966424/f1a36f8a-0d87-49ea-9ee2-aa55840b4a72)
### Category: Arithmetic and Statistical Operations
 ![image](https://github.com/Ahmed-abdelgalil/AWS-AI-Programming-with-Python/assets/103966424/655657a6-d100-450e-8a4d-de23db47d3ba)




