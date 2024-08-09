# Python for Data Analytics: String Operations

:arrow_left: [Operations](../03_operations/03_operations.md) - [Conditionals](../05_data_structures/05_data_structures.md) :arrow_right:

We have seen some operations we can do in Python for numeric (`int`, `float`) and boolean (`bool`) values.

There is a whole bunch of operations that we can do with strings (`str`) as well.

Not only operations, but also properties and methods that we can use to manipulate strings.

But before that, we are going to present how to define stringas in Python.

## Defining strings

Strings are defined in Python by enclosing the text in single `'` or double `"` quotes.

```python
# single quotes
my_string_single = 'Hello, world!'

# double quotes
my_string_double = "Hello, world!"
```

Both `my_string_single` and `my_string_double` are the same string, the only difference is the way we define them. We can check that they are the same by comparing them:

```python
print(my_string_single == my_string_double)
```

> True

Also, we can define strings with triple quotes `'''` or `"""`. This is useful when we want to define a string that spans multiple lines.

```python
my_string_multi = '''Hello,
world!'''

print(my_string_multi)
```

> Hello,  
world!

The triple quotes will keep the line breaks in the string.

## String operations

There are two main operations that we can do with strings:

* Concatenation: joining two or more strings
* Repetition: repeating a string a number of times

We can concatenate strings with the `+` operator:

```python
my_string = "Daniel" + " " + "Garcia"

print(my_string)
```

> Daniel Garcia

We can repeat a string with the `*` operator, as many times as we want:

```python
my_string = "Alright " * 3

print(my_string)
```

> Alright Alright Alright

Keep in mind that we can't concatenate strings with other types of objects, like numbers. We need to convert them to strings first:

```python
my_string = "The number is " + str(5)

print(my_string)
```

> The number is 5

Or, we can use the `f-string` method to format strings.

## Formatting strings

In Python, we can format strings with the `f-string` method. There are other (older) methods to format strings, but the `f-string` method is the most used and the most readable, in my opinion.

An f-string allows us to insert variables inside a string, and it will replace the variable with its value in the positions we want.

To define an f-string, we need to add an `f` before the string definition, and then we can insert variables inside the string with curly braces `{}`.

```python
name = "Daniel"

my_string = f"My name is: {name}"

print(my_string)
```

> My name is: Daniel

You can see that the placeholder `name` was replaced by its value in the string.

We can include any expression inside the curly braces, not only variables:

```python
my_string = f"5 + 3 = {5 + 3}"

print(my_string)
```

> 5 + 3 = 8

An we can even format the output of the expression:

```python
number = 5 / 3

my_string = f"5 / 3 = {number:.2f}"

print(my_string)
```

> 5 / 3 = 1.67

The `:.2f` part of the expression tells Python to format the number with two decimal places.

## Properties and methods

In Python, everything we can save in a variable is an object.

Just like in real life, objects have properties and methods.

Let's think of a real-life object: a laptop.

A laptop has attributes like `color`, `ram_size`, `screen_size`, etc. These attributes are the properties of the laptop object.

It also has actions associated to it like `turn_on`, `restart`, `reset`, etc. These actions are the methods of the laptop object.

I like to think of properties as nouns and methods as verbs/actions.

In Python, *usually* properties are accessed with a dot `.` followed by the property name, and methods are accessed with a dot `.` followed by the method name and parentheses `()`.

```python
laptop.color # extract the color property

laptop.turn_on() # execute the turn_on method on the laptop object
```

Let now see some properties and methods that we can use with strings.

## String properties

In Python, strings have some properties that we can access, but they are not accesed with a dot `.` as stated before.

Two properties that we will use a lot are:

* `len`: returns the length of the string
* `type`: returns the type of the object

There is a third one that is not a property, but a way to access the characters of a string, the index.

We can calculate the length of a string with the `len` function:

```python
my_string = "Hello, world!"

print(len(my_string))
```

> 13

This means that the string `my_string` has 13 characters, including spaces and punctuation.

## String methods

Strings might have a few properties, but they have a lot of methods we can use.

Just to mention some of them:

* `upper`: converts the string to uppercase
* `lower`: converts the string to lowercase
* `capitalize`: converts the first character of the string to uppercase
* `title`: converts the first character of each word to uppercase
* `strip`: removes leading and trailing whitespaces
* `replace`: replaces a substring with another
* `split`: splits the string into a list of substrings
* `join`: joins a list of strings into a single string

[And many more](https://docs.python.org/3/library/stdtypes.html#string-methods)

Let's see some examples:

```python
my_string = "String Stuff Here"
```

And now we can use the methods:

```python
print(my_string.upper())
```

> STRING STUFF HERE

```python
print(my_string.lower())
```

> string stuff here

```python
print(my_string.capitalize())
```

> String stuff here

```python
print(my_string.title())
```

> String Stuff Here

```python
# notice the leading and trailing whitespaces
my_string = "   String Stuff Here   " 

print(my_string.strip())
```

> String Stuff Here

```python
print(my_string.replace("Stuff", "Things"))
```

> String Things Here

```python
print(my_string.split())
```

> ['String', 'Stuff', 'Here']

```python
my_list_of_strings = ['String', 'Stuff', 'Here']

print(" ".join(my_list_of_strings))
print("-".join(my_list_of_strings))
```

> String Stuff Here  
> String-Stuff-Here

:arrow_left: [Operations](../03_operations/03_operations.md) - [Conditionals](../05_data_structures/05_data_structures.md) :arrow_right:
