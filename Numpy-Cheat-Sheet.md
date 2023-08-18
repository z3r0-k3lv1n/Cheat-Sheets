# NumPy Cheat Sheet

NumPy is a powerful library for numerical computing in Python. It provides support for arrays, matrices, and a wide range of mathematical functions. Here's a cheat sheet with some common NumPy functions:

## Importing NumPy

```python
import numpy as np
```

## Creating Arrays

```python
# 1D array
arr1d = np.array([1, 2, 3, 4, 5])

# 2D array
arr2d = np.array([[1, 2, 3], [4, 5, 6]])

# Zeros array
zeros = np.zeros((2, 3))

# Ones array
ones = np.ones((3, 2))

# Identity matrix
identity = np.eye(3)

# Random array
random_arr = np.random.rand(2, 2)
```

## Array Operations

```python
# Element-wise addition
addition = arr1d + arr1d

# Element-wise multiplication
multiplication = arr1d * 2

# Matrix multiplication
mat_mult = np.dot(arr2d, arr2d.T)

# Transpose
transpose = arr2d.T

# Reshape array
reshaped = arr1d.reshape(5, 1)

# Element-wise functions
sqrt_arr = np.sqrt(arr1d)
exp_arr = np.exp(arr1d)
log_arr = np.log(arr1d)
```

## Indexing and Slicing

```python
# Indexing
element = arr1d[2]

# Slicing
slice_1 = arr1d[1:4]
slice_2 = arr2d[:, 0]

# Boolean indexing
bool_idx = arr1d[arr1d > 2]
```

## Aggregation

```python
# Sum of all elements
total_sum = arr1d.sum()

# Mean
mean_value = arr1d.mean()

# Maximum and Minimum
max_val = arr1d.max()
min_val = arr1d.min()

# Index of max/min element
max_idx = arr1d.argmax()
min_idx = arr1d.argmin()
```

## Broadcasting

```python
# Scalar addition
scalar_addition = arr1d + 10

# Broadcasting with 1D array
broadcasted = arr2d + np.array([10, 20, 30])

# Broadcasting with 2D array
broadcasted_2d = arr2d + np.array([[10], [20]])
```

## Linear Algebra

```python
# Matrix determinant
det = np.linalg.det(arr2d)

# Matrix inverse
inv_matrix = np.linalg.inv(arr2d)

# Eigenvalues and eigenvectors
eigenvalues, eigenvectors = np.linalg.eig(arr2d)
```

## Random Numbers

```python
# Generate random numbers from a normal distribution
random_normal = np.random.normal(0, 1, (3, 3))

# Generate random integers
random_integers = np.random.randint(0, 10, 5)
```

## Saving and Loading

```python
# Save array to a file
np.save('my_array.npy', arr1d)

# Load array from a file
loaded_arr = np.load('my_array.npy')
```

NumPy offers many more functions and capabilities for numerical computing. Check the [NumPy documentation](https://numpy.org/doc/stable/) for a comprehensive reference.

---
**Note:** This cheat sheet is a reference guide and might not cover all scenarios. Always refer to the official documentation and consult with experienced developers for complex projects.

Feel free to create a pull request and customize and format this cheat sheet according to your preferences.

