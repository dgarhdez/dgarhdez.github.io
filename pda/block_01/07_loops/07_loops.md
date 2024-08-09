# Python for Data Analytics: Loops

:arrow_left: [Conditionals](../block_01/06_conditionals/06_conditionals.md) - [Comprehensions](../block_01/08_comprehensions/08_comprehensions.md) :arrow_right:

So far we've seen that we can control the flow of code by using [conditional expressions](../block_01/06_conditionals/06_conditionals.md) like `if`, `elif`, and `else`.

Another way to control the flow of code is by using loops. Loops allow us to execute a block of code multiple times, without having to write the same code over and over again.

There are two main types of loops in Python:

* `for` loops: used to iterate over a sequence (e.g. a list, tuple, or string)
* `while` loops: used to execute a block of code as long as a certain condition is met

We can mix loops with conditionals to create more complex programs.

Before diving into loops, let's see some ways to create iterable objects in Python.

## Iterables

An iterable is an object that can be used in a loop. In Python, there are several types of objects that are iterable.

Some of the iterables are the [data structures](../block_01/05_data_structures/05_data_structures.md) that we already know: lists, tuples, strings, sets, dictionaries.

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

Output:
> 0  
1  
2  
3

As you can see, the same syntax requirements we had for `if` statements, apply for `for` loops:

* Start with `for xxx in iterable` and then a colon `:`
* Indent the block of code representing the task(s) to be repeated for each element in the iterable

Let's see the effect of indentation in a `for` loop: printing each character in a string but converted to upper case.

```python
# correct 
my_string = 'hello'

for character in my_string:
    upper_char = character.upper()
    print(upper_char)
```

> H  
E  
L  
L  
O

But if we dont indent the `print` statement, the result changes dramatically:

```python
# incorrect
my_string = 'hello'

for character in my_string:
    upper_char = character.upper()
print(upper_char)
```

> O

What happened is that since the `print` statement is not indented, then Python is not considering that it's a task that should be repeated for every character.

What Python is doing here is letting the loop run for each character, finishes it, and then out of the loop it prints whatever is in `upper_char`, which is the last character in upper case.

So, indentation is crucial.

### Mixing loops and conditionals

We can mix loops with conditionals to create more complex programs.

For example, let's print the numbers from 0 to 9, but only the even numbers:

```python
for number in range(10):
    if number % 2 == 0:
        print(number)
```

> 0  
2  
4  
6  
8  

Or, given a string, let's print each character in the string but only if it's a vowel:

```python
my_string = 'hello'

for character in my_string:
    if character in 'aeiou': # check for vowels
        print(character)
```

> e  
o

### Nested loops

Just like we did with conditionals, we can nest loops inside other loops.

Keep in mind that we will need to indent the inner loop one more level than the outer loop.

For example, given two lists of characters, we can print all the possible combinations of pairs of characters:

```python
list1 = ['a', 'b']
list2 = ['x', 'y']

for char1 in list1:
    for char2 in list2:
        print(char1 + char2)
```

> ax  
ay  
bx  
by

## `while` loops

If we don't know how many times we need to repeat a task, but rather we need to repeat it as long as a certain condition is met, we can use a `while` loop.

The syntax of a `while` loop is:

```python
while condition:
    # code block to be executed
    # as long as the condition is True
    # change the condition inside the loop at some point
```

The key here is that the condition must be `True` at the beginning, and at some point inside the loop it needs to change the condition to `False` to stop the loop.

Let's see an example: print the numbers from 0 to 5 using a `while` loop:

```python
number = 0

while number < 6:
    print(number)
    # using the += operator to increment the number by 1
    number += 1
```

> 0  
1  
2  
3  
4  
5

You can see that the condition (`number < 6`) is `True` at the beginning, and at some point inside the loop, the number is incremented by 1, so the condition will eventually be `False` and the loop will stop.

Let's check step by step how the while loop works:

| `number` | `number < 6` | `print(number)`? | `number += 1` |
|----------|--------------|-----------------|---------------|
| 0        | True         | Yes               | 1             |
| 1        | True         | Yes               | 2             |
| 2        | True         | Yes               | 3             |
| 3        | True         | Yes               | 4             |
| 4        | True         | Yes               | 5             |
| 5        | True         | Yes               | 6             |
| 6        | False        | No                |               |

As mentioned, the condition is True for a while, but at some point, the number is 6, so the condition is False and the loop stops.

### Infinite `while` loops

We should always be careful with `while` loops, because if the condition never changes from `True` to `False`, then the loop will run forever.

This is called an infinite loop, and it can crash your program or your computer, or you can incur in a high cost in cloud services.

For example, the following code will run forever:

```python
number = 0

while number < 6:
    print(number)
    # the number is never incremented
```

Since there condition is always `True`, the loop will run forever.

To stop an infinite loop, you can use the `Ctrl + C` keyboard shortcut, or you can stop the execution of the cell in Jupyter Notebook.

## Altering the flow of loops

We can manually bypass the cbehavior of a loop using the `break` and `continue` statements.

* `break`: stops the loop and exits it immediately
* `continue`: skips the rest of the code block and goes to the next iteration

Let's see an example of `break`: given the first 1000 positive integers, we want to print the all the numbers until we find a number greater than 5:

```python
numbers = range(1, 1001)

for number in numbers:
    if number > 5:
        break
    print(number)
```

> 1  
2  
3  
4  
5  

As you can see, the loop stops when it finds the number 6, and the loop is exited immediately.

A similar behavior can be achieved with `continue`: print the numbers from 1 to 9 skipping all the even numbers:

```python
for number in range(1, 10):
    if number % 2 == 0:
        continue
    print(number)
```

> 1  
3  
5  
7  
9

In this case, the loop skips the `print` statement for even numbers, and goes to the next iteration, by using the `continue` statement.

## Looping through special iterables and objects

We can use loops to iterate over special objects like `range`, `enumerate`, `zip`, and the `items` method of dictionaries.

Let's see some examples:

* Loop through a `range` object: we don't need to convert it to a list to iterate over it.

    ```python
    for number in range(4):
        print(number)
    ```

    > 0  
    1  
    2  
    3  

* Loop through an `enumerate` object: we can use the `enumerate` object directly in the loop, by using two variables in the `for` statement.

    ```python
    my_list = ['a', 'b', 'c']

    for index, value in enumerate(my_list):
        print(index, value)
    ```

    > 0 a  
    1 b  
    2 c

* Loop through a `zip` object: we can use the `zip` object directly in the loop, by using two variables in the `for` statement.

    ```python
    my_list1 = ['a', 'b', 'c']
    my_list2 = [1, 2, 3]

    for value1, value2 in zip(my_list1, my_list2):
        print(value1, value2)
    ```

    > a 1  
    b 2  
    c 3  

* Loop through the `items` method of dictionaries: we can use the `items` method directly in the loop, by using two variables in the `for` statement.

    ```python
    my_dict = {'a': 1, 'b': 2, 'c': 3}

    for key, value in my_dict.items():
        print(key, value)
    ```

    > a 1  
    b 2  
    c 3

:arrow_left: [Conditionals](../block_01/06_conditionals/06_conditionals.md) - [Comprehensions](../block_01/08_comprehensions/08_comprehensions.md) :arrow_right:
