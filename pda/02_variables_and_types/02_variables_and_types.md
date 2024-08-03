# Python for Data Analytics: Variables and types in Python

:arrow_left:[Basics](../01_basics/01_basics.md) - [Variables and Types](../02_variables_and_types/02_variables_and_types.md):arrow_right:

The first thing we need to know Python is how to store data.

We can of course do operations without storing data or the results, but that's not very useful if we need to use the results later on.

##  Variables

In Python, we can store data in variables. A variable is a name that we assign to a piece of data, and it is unique in the context of the program. This name is the one we can use to refer to the data later on, as many times as we need.

To assign a value to a variable, we use the `=` operator. The syntax is as follows:

```python
my_first_variable = 5
```

In this case, we are assigning the value `5` to the variable `_my_first_variable`.

Keep in mind that in Python, variables are case sensitive, so `_my_first_variable` is different from `_My_first_variable`.

### Printing variables

We can print the value of a variable using the `print()` function:

```python
my_first_variable = 5

print(my_first_variable)
```

> 5

This will print `5` to the console, or wherever the output is redirected.

### Naming variables

We can name variables as we want, but I always recommend that the name should be descriptive of the information it contains. This will make the code more readable and easier to understand.

If we are creating a variable to hold thenumber of eggs per carton, then we should name it `eggs_per_carton` instead of `x`, or `eggs`, so that the humans reading our code know what to expect.

There are some hard rules for naming variables in Python, though:

* The first character must be a letter or an underscore.
* The rest of the name can be letters, numbers or underscores.
* The name cannot be a reserved word in Python like `if`, `else`, `for`, `while`, etc.

We will use a specific formatting for our variables called `snake_case`. There are other formats:

* snake_case: lowercase words separated by underscores (`my_first_variable`, which is the one we will use for variables and functions)
* camelCase: words are capitalized except the first one (`myFirstVariable`)
* PascalCase: words are capitalized (`MyFirstVariable`, which is the one we will use for classes if we need them)
* kebab-case: lowercase words separated by hyphens (`my-first-variable`)

More on this in [PEP 8](https://peps.python.org/pep-0008/#descriptive-naming-styles).

### Storing the result of an operation

We can store the result of an operation in a variable, and then use it later on:

```python
my_first_variable = 5

my_second_variable = 3

result = my_first_variable + my_second_variable

print(result)
```

> 8

More on operations in [3. Operations](../03_operations/03_operations.md).

### Understanding variables

We can think of variables as labelled boxes where we can store data. We can put data in them, take data out of them, and even change the data inside them.

In reality, variables are references to memory locations where the data is stored. When we assign a value to a variable, Python will create a memory location, store the data there, and then assign the reference to the variable.

So basically, variables are addresses to memory locations where the data is stored. This is why we can change the data in a variable, and the reference will still be the same.

## Interlude: comments

If Python, whenever we want to include a comment in our code, we use the `#` character. This will tell Python to ignore the rest of the line, so we can write whatever we want after it.

Comments are very useful to explain why are doing something, or to remember what we were thinking when we wrote the code.

```python
# This is a comment
my_first_variable = 5  # This is another comment
```

## Types

What kind of data can we store in a variable? Python can handle many types of data, but the most common ones are:

| Type | Name | What it stores | Example |
|------|-------------|---------|
| `int` | Integer | Whole numbers | `5` |
| `float` | Float | Decimal numbers | `3.14` |
| `str` | String | Text | `'Hello, world!'` |
| `bool` | Boolean | True or False | `True` |

We can check the type of a variable using the `type()` function:

```python
my_first_variable = 5

print(type(my_first_variable))
```

> `<class 'int'>`

This will print `<class 'int'>` to the console, indicating that the variable `my_first_variable` is an integer.

Each type has its own operations and methods, and we will see them in the next sections.

Let's see some examples of each type:

### Type conversion

We can (sometimes) convert a variable from one type to another using the type name as a function.

For example, we can convert a integer to a float using the `float()` function:

```python
my_int_variable = 5

my_float_variable = float(my_int_variable)

print(my_float_variable)
```

> 5.0

This will print `5.0` to the console, indicating that the variable `my_float_variable` is a float.

We can also convert a float to an integer using the `int()` function:

```python
my_float_variable = 3.14

my_int_variable = int(my_float_variable)

print(my_int_variable)
```

> 3

This will print `3` to the console, indicating that the variable `my_int_variable` is an integer. Keep in mind that the decimal part is truncated, not rounded, so don't use `int` to round numbers.

Also, we can convert a number to a string using the `str()` function:

```python
my_int_variable = 5

my_str_variable = str(my_int_variable)

print(my_str_variable)
```

> '5'

This will print `'5'` to the console, indicating that the variable `my_str_variable` is a string. Although for us, humans -- hopefully--, it's the same, for Python it's a different type. Python and other programming languages are very strict about types, so we need to be careful when converting between them.

### Type coercion

Sometimes, Python will convert a variable from one type to another automatically. This is called type coercion, and it happens when we mix types in an operation.

In general, Python will convert the less precise type to the more precise one. For example, if we add an integer and a float, Python will convert the integer to a float and then add them.

This adds safety but also can lead to unexpected results, so we need to be careful when mixing types.

:arrow_left:[Basics](../01_basics/01_basics.md) - [Variables and Types](../02_variables_and_types/02_variables_and_types.md):arrow_right:
