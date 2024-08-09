# Python for Data Analytics: Data Structures

:arrow_left: [String Operations](../04_string_operations/04_string_operations.md) - [Conditionals](../06_conditionals/06_conditionals.md) :arrow_right:

Let's recap the main concepts we've learned so far:

* We can store values of different types in variables.
* We can perform operations with these values using arithmetic, logical, and comparison operators.

The question now is, when I need to store several values, how can I do that?

An use case for this would be if you have a form posted on a website, and you need to store the values of the form fields. You could use a variable for each field, but that would be cumbersome, because you'd probably want to keep all the info related to each field together.

That's why we have data structures in Python.

Data structures are a way to store and organize data in a computer so that it can be used efficiently.

According to our needs, we will use different data structures.

In our case, we are going to focus in the following data structures:

* Lists
* Tuples
* Sets
* Dictionaries

The main differences and similarities between them are according to their mutability and the way we access their elements.

| Data Structure | Mutable | Ordered | Access by index | Access by key | Function |
|----------------|---------|---------|-----------------|--------------|---|
| List | Yes | Yes | Yes | No | `list()` |
| Tuple | No | Yes | Yes | No | `tuple()` |
| Set | Yes | No | No | No | `set()` |
| Dictionary | Yes | Yes* | No | Yes | `dict()` |

\* Since Python 3.7, dictionaries are ordered.

Let's see each data structure in detail.

## Index and position

Before we start, let's clarify the concepts of index and position.

For a human, the position represents the place where an element is located in a sequence. For example, in a ranking of runners, the best is in the first position, the second best in the second position, and so on. So, for us, positions start at 1.

For computers, we don't use the concept positions, we use the concept of index.

In Python, the index represents the place where an element is located in a sequence. The difference is that for Python, the index starts at 0.

So, the comparison between positions and indexes is:

| Position | Index |
|----------|-------|
| 1 | 0 |
| 2 | 1 |
| 3 | 2 |
| 4 | 3 |
| ... | ... |

We say Python is a zero-based language because it uses zero-based indexing.

## Lists

| Data Structure | Mutable | Ordered | Access by index | Access by key | Function |
|----------------|---------|---------|-----------------|--------------|---|
| List | Yes | Yes | Yes | No | `list()` |

Lists are the most versatile data structure in Python. They can store any type of data, and they are mutable, which means we can change their elements. Also, each element is stored in a specific position, so we can access them by their index.

We define lists using square brackets `[]` and separating the elements with commas `,`.

Let's see an example:

```python
my_list = [1, 2, 3, 4, 5]

print(my_list)
```

> Output: `[1, 2, 3, 4, 5]`

### Lists properties and methods

Lists have several properties and methods that we can use to manipulate them.

#### Calculating the length of a list: `len()`

```python
my_list = [1, 2, 3, 4, 5]

print(len(my_list))
```

> Output: `5`

#### Adding elements to a list: `append()`

```python
my_list = [1, 2, 3, 4, 5]

my_list.append(6)

print(my_list)
```

> Output: `[1, 2, 3, 4, 5, 6]`

#### Adding elements to a list in a specific position: `insert()`

```python
my_list = [1, 2, 3, 4, 5]

my_list.insert(2, 2.5)

print(my_list)
```

> Output: `[1, 2, 2.5, 3, 4, 5]`

#### Removing elements from a list: `remove()`

```python
my_list = ["a", "b", "c", "d", "e"]

my_list.remove("c")

print(my_list)
```

> Output: `['a', 'b', 'd', 'e']`

#### Removing elements from a list by index: `pop()`

By default, it removes the last element if no index is provided.

```python
my_list = ["a", "b", "c", "d", "e"]

my_list.pop(2)

print(my_list)
```

> Output: `['a', 'b', 'd', 'e']`

Also, `pop()` returns the removed element.

```python
my_list = ["a", "b", "c", "d", "e"]

removed_element = my_list.pop()

print(removed_element)
```

> Output: `e`

#### Changing elements in a list

```python
my_list = [1, 2, 3, 4, 5]

my_list[2] = 10 # change the element in the third position

print(my_list)
```

> Output: `[1, 2, 10, 4, 5]`

## Tuples

| Data Structure | Mutable | Ordered | Access by index | Access by key |
|----------------|---------|---------|-----------------|--------------|
| Tuple | No | Yes | Yes | No |

Tuples are similar to lists, in the sense that they can store any type of data.

The main difference is that tuples are immutable, which means we can't change their elements. Also, each element is stored in a specific position, so we can access them by their index.

We define tuples using parentheses `()` and separating the elements with commas `,`.

Let's see an example:

```python
my_tuple = (1, 2, 3, 4, 5)

print(my_tuple)
```

> Output: `(1, 2, 3, 4, 5)`

### Tuples properties and methods

Tuples have fewer properties and methods than lists, because they are immutable.

#### Calculating the length of a tuple: `len()`

```python
my_tuple = (1, 2, 3, 4, 5)

print(len(my_tuple))
```

> Output: `5`

## Sets

| Data Structure | Mutable | Ordered | Access by index | Access by key | Function |
|----------------|---------|---------|-----------------|--------------|---|
| Set | Yes | No | No | No | `set()` |

Sets are a very useful data structure, because their main property is that they don't allow repeated elements.

Also, they are mutable, which means we can change their elements.

Sets are unordered, which means we can't access their elements by index or key.

We define sets using curly braces `{}` and separating the elements with commas `,`.

Let's see an example:

```python
my_set = {1, 2, 2, 3, 4, 4, 5}

print(my_set)
```

> Output: `{1, 2, 3, 4, 5}`

As you can see, the repeated elements were removed.

### Sets properties and methods

Sets have several properties and methods that we can use to manipulate them.

#### Calculating the length of a set: `len()`

```python
my_set = {1, 2, 3, 4, 5}

print(len(my_set))
```

> Output: `5`

#### Adding elements to a set: `add()`

```python
my_set = {1, 2, 3, 4, 5}

my_set.add(6)

print(my_set)
```

> Output: `{1, 2, 3, 4, 5, 6}`

#### Removing elements from a set: `remove()`

```python
my_set = {1, 2, 3, 4, 5}

my_set.remove(3)

print(my_set)
```

> Output: `{1, 2, 4, 5}`

#### Adding single elements: `set()`

```python
my_set = {1, 2, 3, 4, 5}

my_set.add(6)

print(my_set)
```

> Output: `{1, 2, 3, 4, 5, 6}`

#### Adding elements from another data structure: `update()`

```python
my_set = {1, 2, 3, 4, 5}

my_set.update([6, 7, 8])

print(my_set)
```

> Output: `{1, 2, 3, 4, 5, 6, 7, 8}`

### Set operations

Sets have several operations that we can use to manipulate them.

#### Union

Returns a new set with all elements from both sets.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.union(set2))
```

> Output: `{1, 2, 3, 4, 5}`

You can also use the `|` operator.

```python
print(set1 | set2)
```

#### Intersection

Returns a new set with elements that are in both sets.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.intersection(set2))
```

> Output: `{3}`

You can also use the `&` operator.

```python
print(set1 & set2)
```

#### Difference

Returns a new set with elements that are in the first set but not in the second set.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.difference(set2))
```

> Output: `{1, 2}`

You can also use the `-` operator.

```python
print(set1 - set2)
```

#### Symmetric difference

Returns a new set with elements that are in one of the sets but not in both.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

print(set1.symmetric_difference(set2))
```

> Output: `{1, 2, 4, 5}`

You can also use the `^` operator.

```python
print(set1 ^ set2)
```

## Dictionaries

| Data Structure | Mutable | Ordered | Access by index | Access by key | Function |
|----------------|---------|---------|-----------------|--------------|---|
| Dictionary | Yes | Yes* | No | Yes | `dict()` |

\* Ordered since Python 3.7.

Dictionaries are a very useful data structure, because they allow us to store data in key-value pairs.

We define dictionaries using curly braces `{}` and separating the key-value pairs with commas `,`. Each key-value pair is separated by a colon `:`.

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}
```

We can see that I'm storing 3 different pieces of information (`dani`, `36`, `Istanbul`), with 3 different labels (`name`, `age`, `city`), in the same data structure.

### Dictionaries properties and methods

Dictionaries have several properties and methods that we can use to manipulate them.

#### Length of a dictionary: `len()`

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(len(my_dict))
```

> Output: `3`

#### Extracting the keys of a dictionary: `keys()`

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict.keys())
```

> Output: `dict_keys(['name', 'age', 'city'])`

#### Extracting the values of a dictionary: `values()`

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict.values())
```

> Output: `dict_values(['Dani', 36, 'Istanbul'])`

#### Extracting the key-value pairs of a dictionary: `items()`

This method returns a list of tuples.

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict.items())
```

> Output: `dict_items([('name', 'Dani'), ('age', 36), ('city', 'Istanbul')])`

#### Removing an element from a dictionary: `pop()`

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

my_dict.pop("age")

print(my_dict)
```

> Output: `{'name': 'Dani', 'city': 'Istanbul'}`

#### Adding new elements to a dictionary: `update()`

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

my_dict.update({"country": "Turkey"})
my_dict.update({"age": 37})

print(my_dict)
```

> Output: `{'name': 'Dani', 'age': 37, 'city': 'Istanbul', 'country': 'Turkey'}`

## Indexing and slicing

We can access elements in lists, tuples, and strings using indexing and slicing.

### Indexing

Indexing is how we access a specific element in a data structure that is ordered.

We use square brackets `[]` to access an element by its index.

Remember that Python is a zero-based language, so the first element is at index 0.

#### Extracting the first element

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[0])
```

> Output: `1`

#### Extracting the last element

For extracting the last element, we can use the index `-1`.

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[-1])
```

> Output: `5`

Also, we can use the `len()` function to extract the last element.

```python
my_list = [1, 2, 3, 4, 5]

last_index = len(my_list) - 1

print(my_list[last_index])
```

> Output: `5`

####  Extracting central elements

We can extract elements from the middle of the list.

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[2])
```

> Output: `3`

####  Negative indexes

We can also use negative indexes to access elements from the end. For example, the 3rd element (index `2`) from the end is index `-3`.

```python
my_list = [1, 2, 3, 4, 5]

my_list[-3] == my_list[2]
```

> Output: `True`

### Slicing

Slicing is how we extract a subset of elements from a data structure that is ordered.

We use square brackets `[]` and a colon `:` to extract a slice of elements. The syntax is `[start:stop:step]`.

* `start`: the index where the slice starts, inclusive.
* `stop`: the index where the slice ends, exclusive (the element at this index is not included, but the element before it is).
* `step`: the step between elements in the slice.

The default values are, when not provided:

* `start`: `0`
* `stop`: the end of the list
* `step`: `1`

#### Extracting the first 3 elements

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[0:3])
```

> Output: `[1, 2, 3]`

By default, if we don't provide a `start`, it's considered `0`.

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[:3])
```

> Output: `[1, 2, 3]`

#### Extracting the last 3 elements

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[-3:])
```

> Output: `[3, 4, 5]`

By default, if we don't provide a `stop`, it's considered the end of the list.

#### Extracting the central elements

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[1:4])
```

> Output: `[2, 3, 4]`

Remember that the `stop` index is exclusive, therefore the element at index `4` is not included, but the element at index `3` is.

#### Extracting every other element

We can use the `step` parameter to extract every other element.

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[::2])
```

> Output: `[1, 3, 5]`

#### Reversing a list

We can use a negative step to reverse a list.

```python
my_list = [1, 2, 3, 4, 5]

print(my_list[::-1])
```

> Output: `[5, 4, 3, 2, 1]`

## Extracting elements from a dictionary

We can access elements in a dictionary using the key.

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict["name"])
```

> Output: `Dani`

If the key doesn't exist, we get a `KeyError`.

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict["country"])
```

> Output: `KeyError: 'country'`

Meaning that the key `country` doesn't exist in the dictionary, therefore Python can't provide the value associated with it.

We can avoid this error by using the `get()` method.

```python
my_dict = {"name": "Dani", "age": 36, "city": "Istanbul"}

print(my_dict.get("country"))
```

> Output: `None`

If the key doesn't exist, we get `None`, which is a special value in Python that represents the absence of a value, like a null value.

:arrow_left: [String Operations](../04_string_operations/04_string_operations.md) - [Conditionals](../06_conditionals/06_conditionals.md) :arrow_right:
