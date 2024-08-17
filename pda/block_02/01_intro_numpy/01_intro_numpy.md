# Python for Data Analytics: Intro to Numpy

[Intro to Pandas](../block_02/02_intro_pandas/02_intro_pandas.md) :arrow_right:

Numpy is a Python library that allows us to work with arrays, matrices, and tensors. It is the foundation of many other libraries, like Pandas and Scikit-learn.

We will use Numpy, either by itself or with Pandas, to perform operations with data. These operations can also be done using Python lists, but Numpy is much faster and more efficient.

In this section we will import Numpy now, and we will assume it's already imported in the rest of the examples.

```python
import numpy as np
```

```math
SE = \frac{\sigma}{\sqrt{n}}
```

## Creating arrays

In Numpy we create arrays using the `np.array()` function. This function can receive a list, a tuple, or any other iterable object as an argument.

```python
numbers = np.array([1, 2, 3, 4, 5])

print(numbers)
```

> `[1 2 3 4 5]`

It might look like a list, but it's not. We can check the type of the object using the `type()` function:

```python
print(type(numbers))
```

> `<class 'numpy.ndarray'>`

We can also create arrays with other types and more dimensions:

```python
matrix = np.array([["a", "b", "c"], ["d", "e", "f"]])

print(matrix)
```

> `[['a' 'b' 'c']`  
`['d' 'e' 'f']]`

We can also create ranges of numbers using the `np.arange()` function:

```python
range_numbers = np.arange(0, 10)

print(range_numbers)
```

> `[0 1 2 3 4 5 6 7 8 9]`

Resulting in an array with numbers from 0 to 9.

## Lists vs Arrays

Python lists, [as we already know](../block_01/05_data_structures/05_data_structures.md/#lists) are very flexible and can contain different types of data. But this flexibility comes with a cost: lists are not optimized for numerical operations, and they are not the best option when we need to perform operations with lots of data.

This is because how Python lists are stored in memory.

Each element in a list is a reference to a memory address where the actual data is stored. This means that lists are not contiguous in memory, and this can slow down operations that require accessing multiple elements.

Numpy arrays, on the other hand, are stored in contiguous memory blocks, which makes them faster and more efficient when performing numerical operations.

But, Numpy arrays have some limitations:

* All elements in a Numpy array must be of the same type.
* Numpy arrays have a fixed size, which means that we cannot change the size of an array once it is created.

In the end, we are sacrificing flexibility for speed and efficiency.

## Safe casting

As mentioned before, Numpy arrays can only contain elements of the same type. If we try to create an array with different types, Numpy will cast all elements to the most general type.

```python
mixed = np.array([1, 2, "a", "b"])

print(mixed)
```

> `['1' '2' 'a' 'b']`

If we check the type of the array, we will see that it contains strings:

```python
print(mixed.dtype)
```

> `'<U21'`

This means that the array contains Unicode strings.

We can always convert an integer to a string, but we cannot convert a string to an integer. This is why Numpy casted all elements to strings.

Numpy tries its best to cast all elements to the most general type, but sometimes it can't. In those cases, Numpy will raise an error.

## Arrays

We will use the term `array` to refer to Numpy arrays.

These objects can have one or more dimensions, and they can be created in different ways. The term `array` is mostly used in Computer Science, while the term `tensor` is used in Mathematics, Physics, and Engineering, but they are essentially the same thing.

Depending on the number of dimensions in the array, we can have:

* Scalars: 0-dimensional arrays
  $$ a = 1 $$
* Vectors: 1-dimensional arrays
    $$ v = [1, 2, 3] $$
* Matrices: 2-dimensional arrays
    $$ M = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} $$
* Tensors: n-dimensional arrays
    $$ T = \begin{bmatrix} \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} & \begin{bmatrix} 7 & 8 & 9 \\ 10 & 11 & 12 \end{bmatrix} \end{bmatrix} $$

All of those categories can be considered tensors, but we will use the term `tensor` to refer to arrays with more than 2 dimensions.

### Attributes

Numpy arrays have several attributes that we can use to get information about the array:

* `ndim`: the number of dimensions in the array
* `shape`: the shape of the array
* `size`: the number of elements in the array
* `dtype`: the type of the elements in the array

```python
matrix = np.array([[1, 2, 3], [4, 5, 6]])

print(f"Dimensions: {matrix.ndim}")
print(f"Shape: {matrix.shape}")
print(f"Size: {matrix.size}")
print(f"Type: {matrix.dtype}")
```

> `Dimensions: 2`  
`Shape: (2, 3)`  
`Size: 6`  
`Type: int64`  

### Vectors

Vectors are 1-dimensional arrays. We can create them using lists or tuples:

```python
vector = np.array([1, 2, 3])

print(f"Vector: {vector}")
print(f"Dimensions: {vector.ndim}")
print(f"Shape: {vector.shape}")
print(f"Size: {vector.size}")
print(f"Type: {vector.dtype}")
```

> `Vector: [1 2 3]`  
`Dimensions: 1`  
`Shape: (3,)`  
`Size: 3`  
`Type: int64`

The shape of a vector is `(n,)`, where `n` is the number of elements in the vector.

It has a comma because it's a tuple with one element, and that's how Python represents tuples with one element -- otherwise it would be confused with a simple value in parentheses.

### Matrices

Matrices are 2-dimensional arrays. We can create them using lists of lists:

```python
matrix = np.array([[1, 2, 3], [4, 5, 6]])

print(f"Matrix: {matrix}")
print(f"Dimensions: {matrix.ndim}")
print(f"Shape: {matrix.shape}")
print(f"Size: {matrix.size}")
print(f"Type: {matrix.dtype}")
```

> `Matrix: [[1 2 3]`  
`[4 5 6]]`  
`Dimensions: 2`  
`Shape: (2, 3)`  
`Size: 6`  
`Type: int64`  

The shape of a matrix is `(n, m)`, where `n` is the number of rows and `m` is the number of columns.

Matrices will be the most common object when dealing with data, as they represent tables with rows and columns.

### Tensors

In general, every array is a tensor, but we will use the term `tensor` to refer to arrays with more than 2 dimensions.

We can create tensors using lists of lists of lists:

```python
tensor = np.array([[[1, 2, 3], [4, 5, 6]], [[7, 8, 9], [10, 11, 12]]])

print(f"Tensor: {tensor}")
print(f"Dimensions: {tensor.ndim}")
print(f"Shape: {tensor.shape}")
print(f"Size: {tensor.size}")
print(f"Type: {tensor.dtype}")
```

> `Tensor: [[[ 1  2  3]`  
`[ 4  5  6]]`  
`[[ 7  8  9]`  
`[10 11 12]]]`  
`Dimensions: 3`  
`Shape: (2, 2, 3)`  
`Size: 12`  
`Type: int64`  

The shape of a tensor is `(n, m, o)`, where `n` is the number of matrices, `m` is the number of rows, and `o` is the number of columns.

As the number of dimensions increases, talkinng about rows or columns doesn't make much sense, so we will stick to 2-D matrices when talking about rows and columns.

## Element-wise operations

### Arithmetic operations

When using arrays, in many cases the operations are element-wise and the arithmetic operators work as expected:

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

print(f"Addition: {a + b}")
print(f"Subtraction: {a - b}")
print(f"Multiplication: {a * b}")
print(f"Division: {a / b}")
print(f"Exponentiation: {a ** b}")
print(f"Modulus: {b % a}")
print(f"Floor division: {b // a}")
```

> `Addition: [5 7 9]`  
`Subtraction: [-3 -3 -3]`  
`Multiplication: [ 4 10 18]`  
`Division: [0.25 0.4  0.5 ]`  
`Exponentiation: [  1  32 729]`  
`Modulus: [0 1 0]`  
`Floor division: [4 2 2]`

### Comparison operations

We can also use comparison operators:

```python
a = np.array([1, 2, 3])
b = np.array([4, 2, 1])

print(f"Greater than: {a > b}")
```

> `Greater than: [False False True]`

The comparison operators will return an array of booleans.

The result of a comparison operation can be used to filter elements in an array. This is called boolean indexing or boolean masking.

```python
a = np.array([1, 2, 3])
b = np.array([4, 2, 1])

mask = a > b

masked_a = a[mask] # apply the mask

print(masked_a)
```

> `[3]`

What is happening here is that the `mask` array contains `True` in the position where the condition is `True`, and `False` otherwise.

When we use the `mask` array to index the `a` array, we get only the elements where the condition is `True`, which is the element `3` in our example.

### Logical operations

We can also use logical operators:

```python
a = np.array([True, True, False])
b = np.array([True, False, False])

print(f"Logical AND: {a & b}")
print(f"Logical OR: {a | b}")
print(f"Logical NOT: {~a}")
```

> `Logical AND: [ True False False]`  
`Logical OR: [ True  True False]`  
`Logical NOT: [False False  True]`  

As you can see, the symbols for logical operators are different from the ones we use in Python (`and`, `or`, `not`).

| Python | Numpy |
|--------|-------|
| `and`  | `&`   |
| `or`   | `\|`  |
| `not`  | `~`   |

## Broadcasting

Broadcasting is a powerful feature in Numpy that allows us to perform operations between arrays with different shapes.

When we perform an operation between two arrays with different shapes, Numpy will try to "broadcast" the smaller array to match the shape of the larger array.

For example, we can add a scalar to a vector:

```python
a = np.array([1, 2, 3])
b = 2

print(a + b)
```

> `[3 4 5]`

What Numpy does here is to broadcast the scalar `b` to match the shape of the vector `a`, and then perform the operation.

$$ a = \begin{bmatrix} 1 & 2 & 3 \end{bmatrix} $$
$$ b = 2 \xrightarrow{\text{broadcast}} b_b = \begin{bmatrix} 2 & 2 & 2 \end{bmatrix} $$
$$ a + b = \begin{bmatrix} 1 & 2 & 3 \end{bmatrix} + \begin{bmatrix} 2 & 2 & 2 \end{bmatrix} = \begin{bmatrix} 3 & 4 & 5 \end{bmatrix} $$

We can also add a vector to a matrix:

```python
A = np.array([[1, 2, 3], [4, 5, 6]])
B = np.array([10, 20, 30])

print(A + B)
```

> `[[11 22 33]`  
`[14 25 36]]`

In this case, Numpy broadcasts the vector `b` to match the shape of the matrix `A`:

$$ A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} $$
$$ b = \begin{bmatrix} 1 & 2 & 3 \end{bmatrix} \xrightarrow{\text{broadcast}} B_b = \begin{bmatrix} 10 & 20 & 30 \\ 10 & 20 & 30 \end{bmatrix} $$
$$ A + B_b = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} + \begin{bmatrix} 10 & 20 & 30 \\ 10 & 20 & 30 \end{bmatrix} = \begin{bmatrix} 11 & 22 & 33 \\ 14 & 25 & 36 \end{bmatrix} $$

Broadcasting is very convenient for our operations, but we need to be very careful when using it, as it can lead to unexpected results is the broadcasting happens when we don't want it to.
