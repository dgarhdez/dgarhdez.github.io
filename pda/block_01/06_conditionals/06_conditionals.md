
# Python for Data Analytics: Conditionals

:arrow_left: [Data Structures](../block_01/05_data_structures/05_data_structures.md) - [Loops](../block_01/07_loops/07_loops.md) :arrow_right:

So far we've seen that the code we write is interpreted from top to bottom, but there are times when we want a certain piece of code to be interpreted only when some condition is met. This is where conditionals come in.

## Conditionals

### The `if` statement

In Python, we can use the `if` statement to execute a block of code only if a certain condition is met. The syntax is as follows:

```python
if condition:
    # code to execute if the condition is True
```

* If the condition is `True`, the code block will be executed
* If the condition is `False`, the code block will be skipped

Whatever comes after the `if` must be an expression that evaluates to a boolean (`True` or `False`).

It's mandatory that after the `if` and the condition we add a colon `:`. This is how Python knows that the code block that follows is the one to be executed if the condition is met. The block should also be indented, this means that it should be written with a tab or 4 spaces before the code.

Let's see it with an example:

* Given a string, print it if its length is greater than 5

```python
my_string = "Hello, world!"

if len(my_string) > 5:
    print(my_string)
```

> Hello, world!

In this case, the expression to be evaluated is `len(my_string) > 5`. The `len()` function returns the length of the string, and we compare it to 5.

<pre class="mermaid">
graph LR
    A{length of str\nis greater than 5?} -->|True| B[print my_string]
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

With different strings, the code block will be executed or not depending on the length of the string.

```python
my_string = "Hi!"

if len(my_string) > 5:
    print(my_string)
```

In this case, the code block will not be executed, as the length of the string is less than 5.

<pre class="mermaid">
graph LR
    A{length of str\nis greater than 5?} -->|False| B[Do nothing]
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

### The `else` statement

We've seen that we could print a string if its length was greater than 5. If that's not the case, how can we deal with it?

That's the use case of the `else` statement: doing someting _else_ when the condition is not met:

```python
if condition == True:
    # code to execute if the condition is True
else:
    # do something else if the condition is False
```

Using a similar example as before, we can print a string if its length is greater than 5, and print a different string if it's not:

```python
my_string = "Hi!"

if len(my_string) > 5:
    print(my_string)
else:
    print("The string is too short")
```

> The string is too short

<pre class="mermaid">
graph LR
    A{length of str\nis greater than 5?} -->|True| B[print my_string]
    A -->|False| C[print 'The string is too short']
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

### The `elif` statement

What if we want to check more than one condition? We can use the `elif` statement, which stands for "else if":

This would allow us to try many things, and when one the conditions is met, execute the corresponding code block.

```python
if condition1:
    # code to execute if condition1 is True
elif condition2:
    # code to execute if condition2 is True
elif condition3:
    # code to execute if condition3 is True
else:
    # do something else if none of the conditions are met
```

We can have as many `elif` statements as we want, and the code block will be executed when the corresponding condition is met.

Let's see an example:

* Given a number, if it's greater than 0, print "Positive". If it's less than 0, print "Negative". If it's 0, print "Zero".

```python
my_number = 5

if my_number > 0:
    print("Positive")
elif my_number < 0:
    print("Negative")
else:
    print("Zero")
```

> Positive

How is this code interpreted? Let's see!

<pre class="mermaid">
graph LR
    F[my_number = 5] --> A{number > 0?}
    A -->|True| B[print 'Positive']
    A -->|False| C{number < 0?}
    C -->|True| D[print 'Negative']
    C -->|False| E[print 'Zero']
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

As you see, since the number is 5, it can only be greater than 0, so the code block that prints "Positive" is executed.

## Recap

We can control how the code is executed based on conditions that evaluate as `True` or `False`.

We can check only for the truth of a condition using the `if` statement

```python
if condition:
    # code to execute if the condition is True
```

We can execute a different code block if the condition is not met using the `else` statement

```python
if condition:
    # code to execute if the condition is True
else:
    # do something else if the condition is False
```

We can check multiple conditions using the `elif` statement

```python
if condition1:
    # code to execute if condition1 is True
elif condition2:
    # code to execute if condition2 is True
elif condition3:
    # code to execute if condition3 is True
else:
    # do something else if none of the conditions are met
```

`if` is mandatory, `else` and `elif` are optional.

## Concatenating conditions

We can concatenate conditions using the logical operators `and`, `or` and `not`.

* `and`: Both conditions must be `True` for the whole expression to be `True`
* `or`: At least one of the conditions must be `True` for the whole expression to be `True`
* `not`: Negates the condition

Let's see an example:

* Given a number, if it's greater than 0 and less than 10, print "A".
* If it's lesser or equal than 0, print "B"
* If it's greater than 10, print "C"

```python
my_number = 11

if (my_number > 0) and (my_number < 10):
    print("A")
elif my_number <= 0:
    print("B")
elif my_number > 10:
    print("C")
```

> C

## Nested conditionals

We can check for conditions inside other conditions, this is called nested conditionals.

```python
if condition1:
    if condition2:
        # code to execute if condition1 and condition2 are True
    else:
        # code to execute if condition1 is True and condition2 is False
else:
    # code to execute if condition1 is False
```

Let's do it with an example:

* Given a number, if the number is lesser or equal than 7 then print "Less than 7"

* If it's greater than 7:

  * If it's greater than 10, print "Greater than 10"

  * If it's less or equal than 10, print "Between 7 and 10"

```python
my_number = 5

if my_number <= 7:
    print("Less than 7")
else:
    if my_number > 10:
        print("Greater than 10")
    else:
        print("Between 7 and 10")
```

> Less than 7

<pre class="mermaid">
graph LR
    F[my_number = 5] --> A{number <= 7?};
    A -->|True| B[print 'Less than 7'];
    A -->|False| C{number > 10?};
    C -->|True| D[print 'Greater than 10'];
    C -->|False| E[print 'Between 7 and 10'];
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@10.9.1/dist/mermaid.min.js"></script>

## Using conditionals when defining variables

Let's create a variable `num_sign` that receives "Positive" if a number `my_number` is greater than 0, and "Negative" if it's less than 0.

```python
number = 5

if my_number > 0:
    num_sign = "Positive"
else:
    num_sign = "Negative"

print(num_sign)
```

> Positive

We can do all this in one line using a conditional expression:

```python
num_sign = "Positive" if my_number > 0 else "Negative"

print(num_sign)
```

> Positive

In the end we are using the same logic, but in a more concise way, and it's easier to read, it's almost like reading a sentence in English.

:arrow_left: [Data Structures](../block_01/05_data_structures/05_data_structures.md) - [Loops](../block_01/07_loops/07_loops.md) :arrow_right:
