# What is Python?

> ## Learning Objectives

> * Different Python environments
> * Python commands
> * Math operators
> * Python Strings

## What is Python?

Python was created in the late 1980s, primarily as a teaching and _scripting_ language. Python has since become an essential tool for many programmers, engineers, researchers, and data scientists across academia and industry. Accordingly, a large _ecosystem_ of discipline-specific tools have been built on top of it. Part 2 of this course will introduce you to the Scientific Python Stack (SciPy) a collection of open source software for scientific computing in Python.

## Python prompt

The traditional, pehaps still the default way to to start using Python, is to open up a _command line_ on your computer. From here, opening up a _Python_ session is usually as easy as typing `python` into the command prompt and hitting `enter`.

```bash
$ python
```

Here is a representative output of what you might see when you launch Python, namely a brief summary of which distribution and version of Python you are using.

```
Python 2.7.9 (default, Mar  1 2015, 12:57:24)
[GCC 4.9.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
```

## Your first Python command!

After running the `python` command in the _command line_ the prompt changed to `>>>`. This means that for now we may only use commands in the Python language. You don't have to type in `>>>` - Python will do that for you.

If you want to exit the Python console at any point, just type `exit()` or use the shortcut `Ctrl + Z` for Windows and `Ctrl + D` for Mac/Linux. Then you won't see `>>>` any longer.

For now, we don't want to exit the Python console. We want to learn more about it. Let's start with something really simple. For example, try typing some math, like `2 + 3` and hit `enter`.

```python
2 + 3
```
```
5
```

Nice! See how the answer popped out? Python knows math! You could try other commands like:
- `4 * 5`
- `5 - 1`
- `40 / 2`

As you can see, Python is a great calculator. If you're wondering what else you can do...here is a quick overview of the common mathematical operators:

- `+` (plus)
    - Adds two objects
    - `3 + 5` gives `8`.

- `-` (minus)
    - Gives the subtraction of one number from the other; if the first operand is absent it is assumed to be zero.
    - `-5.2` gives a negative number and `50 - 24` gives `26`.

- `*` (multiply)
    - Gives the multiplication of the two numbers or returns the string repeated that many times.
    - `2 * 3` gives `6`.

- `**` (power)
    - Returns x to the power of y
    - `3 ** 4` gives `81` (i.e. `3 * 3 * 3 * 3`)

- `/` (divide)
    - Divide x by y
    - `13 / 3` gives `4.333333333333333`

- `//` (divide and floor)
    - Divide x by y and round the answer _down_ to the nearest whole number
    - `13 // 3` gives `4`
    - `-13 // 3` gives `-5`

- `%` (modulo)
    - Returns the remainder of the division
    - `13 % 3` gives `1`. `-25.5 % 2.25` gives `0.75`.

## Evaluation Order

If you had an expression such as `2 + 3 * 4`, is the addition done first or the multiplication and does it matter? It certainly does matter, and Python will obediently follow the convention that the multiplication should be done first. Alternatively we can use round brackets `()` to override the default operator _precedence_, as well as making our code easier to follow.

## Numbers

We've begun using numbers in python and it seems pretty straight forward. However, let's pause for a moment and observe that not all number are created equal. In fact, there are a _number of types of numbers_ in Python. Let's verify this, before we move on:

```python
type(2)
```
An examples of an integer is `2` which is just a whole number.

```python
type(2.0)
```

In programming we call decimal numbers floating point numbers (or _floats_ for short). Also what happened when we wrote `type(2)`? We used a _function_ and we will return to what these are later in the course. You also might wonder why the need for multiple types of number in Python. In fact, it is very useful. If you wrote a program that counted people as they scanned their tickets at a concert, would you be better off using integers or floating point numbers?


## Strings

How about your name? Type your first name in quotes like this:

```python
"rick astley"
```
    'rick astley'

You've now created your first string! It's a sequence of characters that can be processed by a computer. The string must always begin and end with the same character. This may be single (`'`) or double (`"`) quotes (there is no difference!) The quotes tell Python that what's inside of them is a string.

Strings can be strung together (or concatenated). Try this:

```python
"Hi there " + "Rick"
```
```
'Hi there Rick'
```

You can also multiply strings with a number:

```python
"Rick" * 3
```
```
'RickRickRick'
```

Nice, huh? To see your name in uppercase letters, simply type:

```python
"Rick".upper()
```
```
'RICK'
```

You just used the `upper` __method__ on your string! A method (like `upper()`) is a sequence of instructions that Python performs on a given object (`"Rick"`), once you call it. The notation `x.method()` reminds us that the method is attached or belongs to the data type `x`.

If you want to know the number of letters contained in your name, there is a __function__ for that too!

```python
len("Rick")
```
```
4
```
Wonder why sometimes you call functions with a `.` at the end of a string (like `"Ola".upper()`) and sometimes you first call a function and place the string in parentheses? Well, in some cases, functions belong to objects, like `upper()`, which can only be performed on strings. In this case, we call the function a __method__. Other times, functions don't belong to anything specific and can be used on different types of objects, just like `len()`. That's why we're giving `"Rick"` as a parameter to the `len` function. 


## Errors

Let's try something new. Can we get the length of a number the same way we could find out the length of our name? Type in `len(304023)` and hit `enter`:

```python
len(304023)
```    
```
Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
TypeError: object of type 'int' has no len()
```
We got our first error! It says that objects of type "int" (integers, whole numbers) have no length. So what can we do now? Maybe we can write our number as a string? Strings have a length, right?

```Python
len(str(304023))
```
6

It worked! We used the `str` function inside of the `len` function. `str()` converts everything to strings.

- The `str` function converts things into __strings__
- The `int` function converts things into __integers__

> Important: we can convert numbers into text, but we can't necessarily convert text into numbers - what would `int('hello')` be anyway?



<!--
## Summary

OK, enough of strings. So far you've learned about:

- __the prompt__ - typing commands (code) into the Python prompt results in answers in Python
- __numbers and strings__ - in Python numbers are used for math and strings for text objects
- __operators__ - like + and \*, combine values to produce a new one
- a little look at __functions__ - like upper() and len(), that perform actions on objects.
- __errors__
- __Jupyter notebooks__

These are the basics of every programming language you learn.

-->
