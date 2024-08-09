# Python for Data Analytics: Error catching

:arrow_left: [Functions](../block_01/09_functions/09_functions.md) - [Intro to Numpy](../block_01/11_intro_numpy/11_intro_numpy.md) :arrow_right:

When everything works, our programs will run and will return the expected results.

But there are times when our programs will fail. Luckily Python provides with very good error and exception handling mechanisms.

In this section we will learn how to handle errors and exceptions in Python.

## Error messages

When an error occurs in Python, the interpreter will raise an exception and will print an error message that will help us understand what went wrong.

There are many types of exceptions in Python, but some of the most common are:

* `SyntaxError`: raised when the code has a syntax error
* `NameError`: raised when a variable is not defined
* `TypeError`: raised when an operation is performed on an object of an inappropriate type
* `ValueError`: raised when a function receives an argument of the correct type, but with an inappropriate value
* `ZeroDivisionError`: raised when the second argument of a division or modulo operation is zero
* `KeyError`: raised when a dictionary does not have a key
* ...

We should always read the error message carefully, as it will help us understand what went wrong, and where in the code the error occurred.

Let's create a bug in our code to see how Python raises an exception:

```python
def divide(a, b):
    return a / b

print(divide(10, 0))
```

> `ZeroDivisionError: division by zero`

It's very clear what is happening here: we are trying to divide a number by zero, which is not allowed in Python.

One way we have to deal with this is to avoid this situation by checking if the divisor is zero before performing the division:

```python
def divide(a, b):
    # avoid division by zero
    if b == 0:
        return "Division by zero is not allowed"
    return a / b

print(divide(10, 0))
```

> `Division by zero is not allowed`

```python
print(divide(10, 2))
```

> `5.0`

So we are covered.

But there are times when we can't avoid an error, and we need to handle it when it occurs. Or even worse, we don't know what kind of error will occur, and we need to handle all of them.

This is where error catching comes in.

## Error catching

Python provides a way to handle exceptions using the `try` and `except` blocks.

They are similar to `if` and `else` blocks, but they are used to catch exceptions.

The general syntax is:

```python
try:
    # code that may raise an exception
except:
    # code to handle the exception
```

Where:

* The `try` block contains the code that **may** raise an exception.
* The `except` block contains the code that will be executed if an exception is raised, our error handling code.

Let's see an example:

```python
def divide(a, b):
    try:
        return a / b
    except:
        return "Division by zero is not allowed"

print(divide(10, 0))
```

> `Division by zero is not allowed`

This solution is better than the previous one, as we are handling any exception that may occur when dividing two numbers.

Let's complicate it a bit more by dividing a number by a string:

```python
print(divide(10, "a"))
```

In this case, we will get the same error message `"Division by zero is not allowed"`. And that's not what happened.

So the idea is to catch the specific exception that we want to handle, and do something different for each exception when it occurs.

```python
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Division by zero is not allowed"
    except TypeError:
        return "Division using non-numeric values is not allowed"

print(divide(10, "a"))
```

> `Division by a non-numeric value is not allowed`

Now we have it.

We can also catch all exceptions in a single block, with a generic message:

```python
def divide(a, b):
    try:
        return a / b
    except Exception as e:
        return f"An error occurred: {e}"

divide(10, "a")
```

> `An error occurred: unsupported operand type(s) for /: 'int' and 'str'`

By catching the general exception `Exception`, we are able to catch any exception that may occur in the `try` block, and provide a generic message to the user.

This is useful when we don't know what kind of exception may occur, or when we don't want to handle each exception separately.

## `else` and `finally` blocks

We can also use the `else` and `finally` blocks with the `try` block.

* The `else` block will be executed if no exception is raised in the `try` block.
* The `finally` block will be executed no matter what, even if an exception is raised.

Let's see an example:

```python
def divide(a, b):
    try:
        result = a / b
    except ZeroDivisionError:
        return "Division by zero is not allowed"
    except TypeError:
        return "Division using non-numeric values is not allowed"
    else:
        return result
    finally:
        print("Division operation finished")

print(divide(10, 2))
```

> `Division operation finished`  
`5.0`

```python
print(divide(10, "a"))
```

> `Division operation finished`  
`Division using non-numeric values is not allowed`

We can see that the `finally` block is always executed, no matter what. Then, if no exception is raised, the `else` block is executed.

This is useful when we need clear operations to be executed after the `try` block, no matter what.

:arrow_left: [Functions](../block_01/09_functions/09_functions.md) - [Intro to Numpy](../block_01/11_intro_numpy/11_intro_numpy.md) :arrow_right:
