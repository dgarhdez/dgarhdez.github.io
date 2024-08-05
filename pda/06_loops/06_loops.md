# Python for Data Analytics: Loops

:arrow_left: [Loops](../06_loops/06_loops.md) - [Functions](../07_functions/07_functions.md) :arrow_right:

So far we've seen that we can control the flow of code by using [conditional expressions](../05_conditionals/05_conditionals.md) like `if`, `elif`, and `else`.

Another way to control the flow of code is by using loops. Loops allow us to execute a block of code multiple times, without having to write the same code over and over again.

There are two main types of loops in Python:

* `for` loops: used to iterate over a sequence (e.g. a list, tuple, or string)
* `while` loops: used to execute a block of code as long as a certain condition is met

We can mix loops with conditionals to create more complex programs.

Before diving into loops, let's see some ways to create iterable objects in Python.

## Iterables

An iterable is an object that can be used in a loop. In Python, there are several types of objects that are iterable.

Some of the iterables are the [data structures](../04_data_structures/04_data_structures.md) that we already know: lists, tuples, strings, sets, dictionaries.

But there are others that are new to us:

* `range` objects
* `enumerate` objects
* `zip` objects
* `items` method of dictionaries

### `range` objects

`range` objects are used to generate a sequence of numbers. They are very useful when we want to iterate over a sequence of numbers.

They use the same syntax we know for slicing lists: `range(start, stop, step)`.

```python
my_range = range(0, 10)

print(my_range)
```

> `range(0, 10)`

When printing a `range` object, we see that it is a range from 0 to 10, but it is not a list. This is because `range` objects are not lists, they contain the "recipe" to generate a sequence of numbers without generating it in memory.

So, if want to see the numbers in the range, we need to convert it to a list:

```python
my_range = range(0, 10)

print(list(my_range))
```

> `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`

### `enumerate` objects

`enumerate` objects are used to create a new iterable that contains pairs of values: the index of an element and the element itself.

They are very useful when we want to iterate over a sequence and we need to know the index of each element.

```python
my_list = ['a', 'b', 'c']

print(list(enumerate(my_list)))
```

> `[(0, 'a'), (1, 'b'), (2, 'c')]`

Just like `range` objects, `enumerate` objects are not lists. They contain the "recipe" to generate the pairs of values without generating them in memory.

### `zip` objects

`zip` objects are used to create a new iterable that pairs elements from two or more sequences.

They are very useful when we want to iterate over two or more sequences at the same time.

```python
my_list1 = ['a', 'b', 'c']
my_list2 = [1, 2, 3]

print(list(zip(my_list1, my_list2)))
```

> `[('a', 1), ('b', 2), ('c', 3)]`

Just like `range` and `enumerate` objects, `zip` objects are not lists. They contain the "recipe" to generate the pairs of values without generating them in memory.

### `items` method of dictionaries

The `items` method of dictionaries is used to create a new iterable that pairs keys and values from a dictionary. It's like using `zip` with the keys and values of a dictionary.

```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

print(list(my_dict.items()))
```

> `[('a', 1), ('b', 2), ('c', 3)]`

## `for` loops

When we know how many times we need to repeat a block of code, we can use a `for` loop.

It can be used because we know the amount of iterations, or because we have an iterable object that we want to iterate over.

The syntax of a `for` loop is:

```python
for item in iterable:
    # code block to be executed
    # as many times as there are
    # items in the iterable
```

The iterable can be a predefined list, tuple, string, set, dictionary, or any other iterable object like `range`, `enumerate`, or `zip`.

Let's see some examples:

* Print the numbers from 0 to 3 using a `range` object:

```python
for number in range(4):
    print(number)
```

> 0

> 1

> 2

> 3
