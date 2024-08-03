# Python for Data Analytics: Data Structures

:arrow_left: [Operations](../03_operations/03_operations.md) - [Conditionals](../05_conditionals/05_conditionals.md) :arrow_right:

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

| Data Structure | Mutable | Ordered | Access by index | Access by key |
|----------------|---------|---------|-----------------|--------------|
| List | Yes | Yes | Yes | No |
| Tuple | No | Yes | Yes | No |
| Set | Yes | No | No | No |
| Dictionary | Yes | Yes* | No | Yes |

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

Lists are the most versatile data structure in Python. They can store any type of data, and they are mutable, which means we can change their elements. Also, each element is stored in a specific position, so we can access them by their index.

We define lists using square brackets `[]` and separating the elements with commas `,`.

Let's see an example:

```python
my_list = [1, 2, 3, 4, 5]

print(my_list)
```

> `[1, 2, 3, 4, 5]`
