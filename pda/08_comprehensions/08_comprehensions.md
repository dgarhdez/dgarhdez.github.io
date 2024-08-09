# Python for Data Analytics: Comprehensions

:arrow_left: [Loops](../07_loops/07_loops.md) - [Functions](../09_functions/09_functions.md) :arrow_right:

After learning about data structures, conditionals, and loops, we are now ready to solve these type of problems:

>Given the numbers from 1 to 12, create a list that contains only the even numbers.

Let's solve it step by step.

1. Create a list with the numbers from 1 to 12:

    ```python
    numbers = list(range(1, 13))
    ```

2. Create an auxiliary list to store the even numbers that we will filter from the `numbers` list:

    ```python
    even_numbers = []
    ```

3. Iterate over the `numbers` list and filter the even numbers, storing them in the `even_numbers` list we created:

    ```python
    for number in numbers:
        if number % 2 == 0:
            even_numbers.append(number)
    ````

4. Print the `even_numbers` list:

    ```python
    print(even_numbers)
    ```

Now let's put it all together:

```python
numbers = list(range(1, 13))

even_numbers = []

for number in numbers:
    if number % 2 == 0:
        even_numbers.append(number)

print(even_numbers)
```

> `[2, 4, 6, 8, 10, 12]`

Amazing! We have solved the problem. But we can make it even better.

With list comprehensions, we can solve the same problem in a single line of code:

```python
even_numbers = [number for number in range(1, 13) if number % 2 == 0]

print(even_numbers)
```

> `[2, 4, 6, 8, 10, 12]`

Let's talk about comprehensions.

## Python Comprehensions

Comprehensions are a concise way to create lists, dictionaries, and sets in Python.

We can use them to compress the code and make it more readable, and sometimes even faster.

In general, we can create comprehensions using the same elements we use in loops and conditionals, but in a more compact way.

The general syntax for a list comprehension is:

```python
[expression for item in iterable if condition]
```

Where:

* `expression` is the value that will be added to the new list.
* `item` is the variable that will take the values from the iterable.
* `iterable` is the object that will be iterated over.
* `condition` is an optional filter that will be applied to the items.

Let's see some examples:

* Create a list with the squares of the numbers from 0 to 3:

    ```python
    # with a loop
    squares = []

    for number in range(4):
        squares.append(number ** 2)

    print(squares)
    ```

    > `[0, 1, 4, 9]`

    ```python
    # with a comprehension
    squares = [number ** 2 for number in range(4)]

    print(squares)
    ```

    > `[0, 1, 4, 9]`

* Given a string, create a list with the consonants of the string:

    ```python
    # with a loop
    my_string = 'Daniel Garcia'

    consonants = []

    for char in my_string:
        if char.lower() not in 'aeiou':
            consonants.append(char)
    
    print(consonants)
    ```

    > `['D', 'n', 'l', ' ', 'G', 'r', 'c']`

    ```python
    # with a comprehension
    my_string = 'Daniel Garcia'

    consonants = [char for char in my_string if char.lower() not in 'aeiou']

    print(consonants)
    ```

    > `['D', 'n', 'l', ' ', 'G', 'r', 'c']`

* Given a list of numbers, keep only the numbers that are greater than 5:

    ```python
    # with a loop
    my_list = [1, 6, 2, 7, 3, 8]

    greater_than_5 = []

    for number in my_list:
        if number > 5:
            greater_than_5.append(number)
    
    print(greater_than_5)
    ```

    > `[6, 7, 8]`

    ```python
    # with a comprehension
    my_list = [1, 6, 2, 7, 3, 8]

    greater_than_5 = [number for number in my_list if number > 5]

    print(greater_than_5)
    ```

    > `[6, 7, 8]`

These examples show us how we are using the same elements, but arranged in a more compact way.

### Conditional expressions in comprehensions

We can also use conditional expressions in comprehensions to create more complex results.

The general syntax for a conditional expression in a comprehension is:

```python
[
    expression_1 if expression_condition
    else expression_2
    for item in iterable
    if filter_condition
]
```

Where:

* `expression_1` is the value that will be added to the new list if the `expression_condition` is `True`.
* `expression_2` is the value that will be added to the new list if the `expression_condition` is `False`.
* `expression_condition` is the condition that will determine which expression will be added to the new list.
* `item` is the variable that will take the values from the iterable.
* `iterable` is the object that will be iterated over.
* `filter_condition` is an optional filter that will be applied to the items, if present it's evaluated before the conditional expression `expression_condition`.

Let's see a flowchart to understand how the conditional expression works for this comprehension:

```python
[
    expression_1 if expression_condition
    else expression_2
    for item in iterable
    if filter_condition
]
```

<pre class="mermaid">
graph LR
    F[START: item] --> A{filter_condition == True}
    A -->|False| B[Try next item] --> F
    A -->|True| C{expression_condition == True}
    C -->|True| D[expression_1]
    C -->|False| E[expression_2]
    D --> G[Add to the new list]
    E --> G
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

Let's see some examples:

Given a string, create a new string with the vowels in uppercase and the consonants in lowercase:

```python
# with a loop
my_string = 'testing'

new_string = ''

for char in my_string:
    if char.lower() in 'aeiou':
        new_string += char.upper()
    else:
        new_string += char.lower()

print(new_string)
```

> `'tEstIng'`

```python
# with a comprehension

my_string = 'testing'

new_string = ''.join(
    char.upper() if char.lower() in 'aeiou'
    else char.lower()
    for char in my_string
)

print(new_string)
```

> `'tEstIng'`

We have to use the `join` method to concatenate the characters in the new string, since the comprehension returns a list of characters, not a string

## Dictionary Comprehensions

We can also use dictionaries as the iterable object in comprehensions, or create dictionaries with comprehensions.

The most basic syntax for a dictionary comprehension is:

```python
{
    key_expression: value_expression
    for item in iterable
    if condition
}
```

Where:

* `key_expression` is the expression that will be used as the key in the new dictionary.
* `value_expression` is the expression that will be used as the value in the new dictionary.
* `item` is the variable that will take the values from the iterable.

Let's see it with an example: given the alphabet, create a dictionary where the keys are the characters of the alphabet, and the values are the positions of each letter in the alphabet (look up the `enumerate` function if you don't know it, and how to loop through it in [Loops](../07_loops/07_loops.md/##Looping-through-special-iterables-and-objects)

```python
abc = 'abcdefghijklmnopqrstuvwxyz'

alphabet_positions = {
    char: index
    for index, char in enumerate(abc, start=1) # looping over enumerate elements
}

print(alphabet_positions)
```

> `{'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5, 'f': 6, 'g': 7, 'h': 8, 'i': 9, 'j': 10, 'k': 11, 'l': 12, 'm': 13, 'n': 14, 'o': 15, 'p': 16, 'q': 17, 'r': 18, 's': 19, 't': 20, 'u': 21, 'v': 22, 'w': 23, 'x': 24, 'y': 25, 'z': 26}`
