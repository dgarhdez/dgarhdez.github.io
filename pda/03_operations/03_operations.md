# Python for Data Analytics: Operations

:arrow_left: [Variables and Types](../02_variables_and_types/02_variables_and_types.md) - [Data Structures](../05_data_structures/05_data_structures.md) :arrow_right:

Now that we know the basic types of data and how to store them properly in memory using variables, we can start to perform operations between them.

We will start with arithmetic operations, then move to logical operations, and finally, we will see how to compare values.

## Arithmetic operations

In Python we have the same arithmetic operations as in real life

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `+` | Addition | Adds two numbers | `5 + 3` |
| `-` | Subtraction | Subtracts two numbers | `5 - 3` |
| `-` | Negation | Negates a number | `-5` |
| `*` | Multiplication | Multiplies two numbers | `5 * 3` |
| `/` | Division | Divides two numbers | `5 / 3` |
| `//` | Integer division | Divides two numbers and returns the quotient | `5 // 3` |
| `%` | Modulus | Divides two numbers and returns the remainder | `5 % 3` |
| `**` | Exponentiation | Raises a number to the power of another | `5 ** 3` |

We can use these operators with intergers and floats, and we can mix them without any problem, but if we operate with a float and an integer, the result will always be a float.

Let's see some examples:

* Addition:

```python
a = 5
b = 3

print(a + b)
```

> Output: 8

* Subtraction:

```python
a = 5
b = 3

print(a - b)
```

> Output: 2

* Negation:

```python
a = 5

print(-a)
```

> Output: -5

* Multiplication:

```python
a = 5
b = 3

print(a * b)
```

> Output: 15

* Division:

```python
a = 5
b = 3

print(a / b)
```

> Output: 1.6666666666666667

* Integer division:

```python
a = 5
b = 3

print(a // b)
```

> Output: 1

* Modulus:

```python
a = 5
b = 3

print(a % b)
```

> Output: 2

* Exponentiation:

```python
a = 5
b = 3

print(a ** b)
```

> Output: 125

We will suse these operations left and right, so it's important to understand them well, and to know how to use them properly.

Remember that there is a hyerarchy of operations, in order of precedence:

1. Parentheses
2. Exponentiation
3. Multiplication, Division, Integer Division, Modulus
4. Addition, Subtraction

Let's see an example of this order of precedence:

```python
(5 + 3) * 2 ** 3 - 4
```

First, we solve the parentheses `5 + 3`:

```python
8 * 2 ** 3 - 4
```

Then, we solve the exponentiation `2 ** 3`:

```python
8 * 8 - 4
```

Then, we solve the multiplication: `8 * 8`:

```python
64 - 4
```

Finally, we solve the subtraction: `64 - 4`:

```python
60
```

## Logical operations

Logical operations will help up control the flow of our code as we will see in [5. Conditionals](../06_conditionals/06_conditionals.md).

Logical operators require boolean values, and they return boolean values.

There are 3 logical operators in Python:

| Operator | Name | Example |
|----------|------|---------|
| `not` | Not | `not True` |
| `and` | And | `True and False` |
| `or` | Or | `True or False` |

According to which operator we use, the result will be different:

| Operation | Result |
|-----------|--------|
| `not True` | `False` |
| `not False` | `True` |

| Operation | Result |
|-----------|--------|
| `True and True` | `True` |
| `True and False` | `False` |
| `False and True` | `False` |
| `False and False` | `False` |

| Operation | Result |
|-----------|--------|
| `True or True` | `True` |
| `True or False` | `True` |
| `False or True` | `True` |
| `False or False` | `False` |

And just like with arithmetic operations, we can mix them without any problem, although it's important to know the order of precedence:

1. `not`
2. `and`
3. `or`

Let's see an example of the order of precedence:

```python
not True and True or False
```

First, we solve the `not` operator: `not True`:

```python
False and True or False
```

Then, we solve the `and` operator: `False and True`:

```python
False or False
```

Finally, we solve the `or` operator: `False or False`:

```python
False
```

## Comparison operations

Comparison operations will also help us compare values and control the flow of our code as we will see in [5. Conditionals](../06_conditionals/06_conditionals.md).

Comparisons also will always return a boolean value.

There are 6 comparison operators in Python:

| Operator | Name | Description | Example |
|----------|------|-------------|---------|
| `==` | Equal | Compares if two values are equal | `5 == 3` |
| `!=` | Not equal | Compares if two values are different | `5 != 3` |
| `>` | Greater than | Compares if the first value is greater than the second | `5 > Output: 3` |
| `<` | Less than | Compares if the first value is less than the second | `5 < 3` |
| `>=` | Greater than or equal | Compares if the first value is greater or equal than the second | `5 >= 3` |
| `<=` | Less than or equal | Compares if the first value is less or equal than the second | `5 <= 3` |

We can mix these operators with arithmetic and logical operators, and we can use parentheses to control the order of precedence.

Let's see an example:

```python
(5 + 3) * 2 ** 3 - 4 == 61 and 5 > Output: 3
```

First, we solve the arithmetic operations `(5 + 3) * 2 ** 3 - 4`:

```python
60 == 61 and 5 > Output: 3
```

Then, we solve the comparison operations `60 == 61` and `5 > Output: 3`:

```python
False and True
```

Finally, we solve the logical operation `False and True`:

```python
False
```

:arrow_left: [Variables and Types](../02_variables_and_types/02_variables_and_types.md) - [Data Structures](../05_data_structures/05_data_structures.md) :arrow_right:
