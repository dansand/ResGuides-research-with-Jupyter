
# Variables

> ## Learning Objectives

> *   Assign values to variables
> *   Variables as labels
> *   Gotchas with lists and multiple assigments


Computer programs operate on data. A computer program is a set of statements (i.e., intructions) to accomplish one or more of the following: read, create, calculate, transform, organize, and store data. This goal is achieved through the use of variables. If you think of data as pieces of paper where you wrote something, then a variable is a folder to which you afix a sticker with a name and where you may store one or more pieces of paper.


Let's say we want to create a new variable called `name`:

```python
name = "Ola"
```

As you may have noticed in past lessons, Python didn't return anything like it did before. So how do we know that the variable actually exists? Simply enter `name` and hit `enter`:

```python
name
```
```
'Ola'
```

Yippee! Your first variable :)! You can always change what it refers to:

```python
name = "Sonja"
```

```python
name
```

```
'Sonja'
```

But what if we used the wrong name? Can you guess what would happen? Let's try!

```python
city = "Tokyo"
```

```python
ctiy
```

```
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'ctiy' is not defined
```
An error! As you can see, Python has different types of errors and this one is called a **NameError**. Python will give you this error if you try to use a variable that hasn't been defined yet. If you encounter this error later, check your code to see if you've mistyped any names.


Just like with the string assigned to `name`, our numeric (integer) variable can be printed to the screen:

```python
weight_kg = 55
```


```python
print(weight_kg)
```

```
55
```

We can also do arithmetic with it:

```python
print('weight in pounds:', 2.2 * weight_kg)
```

```python
weight in pounds: 121.0
```



## So what happens behind the scenes?

A variable is a label for a location in memory. It can be used to hold a value. If we imagine the variable as a sticky note with a name written on it, assignment is like putting the sticky note on a particular value:

![Variables as Sticky Notes](../fig/python-sticky-note-variables-01.svg)


In statically typed languages, variables have predetermined types, and a variable can only be used to hold values of that type. Fortuntely for researchers, Python is `dynamically typed`. A language is dynamically typed if the type of a variable is interpreted at runtime: we don't have to tell Python that an integer is an integer, instead, it _interprets our will_.

Any object (Python data type) can be assigned to a variable. Once a variable us instantiated, it can be passed around, handed to functions, queried, altered, etc. They really are fundamental to Python Programming.

## A common gotcha with lists

At this stage, we know about three Python data types, strings, numbers (floats and integers), and lists. We can create variabes as a label for any one of these data types. Let's look a little deeper and see how multiple references to variables can behave a little strangely at times. 

```python
weight_lb = 2.2 * weight_kg
```
```python
print('weight in kilograms:', weight_kg, 'and in pounds:', weight_lb)
```
```
weight in kilograms: 57.5 and in pounds: 126.5
```

![Creating Another Variable](../fig/python-sticky-note-variables-02.svg)

and then change `weight_kg`:

```python
weight_kg = 100.0
print('weight in kilograms is now:', weight_kg, 'and weight in pounds is still:', weight_lb)
```

```
weight in kilograms is now: 100.0 and weight in pounds is still: 126.5
```

![Updating a Variable](../fig/python-sticky-note-variables-03.svg)

Since `weight_lb` doesn't "remember" where its value came from, it isn't automatically updated when `weight_kg` changes. This is different from the way spreadsheets work.

When we write `weight_kg = 100.0`, we're changing `weight_kg` to point to a different (new) object, while `weight_lb` still points at the original object.  

Now let's try a similar excercise with lists:

```python
a = [1,2,3]
b = a
print('a and b are now:', a, b)
```

```
a and b are now: [1, 2, 3] [1, 2, 3]
```
So far so good. Let's make a change to the list represented by the variable `a`:

```python
a[2] = 4
print('but ... they are now both:', a, b)
```

```
but ... they are now both: [1, 2, 4] [1, 2, 4]
```

Assignment statements in Python do not copy objects, they create bindings between a target and an object. Most operations that modify the list will modify it _in place_.  Writing `a[2] = 4  ` does not create a new object. This means that if you have multiple variables that point to the same list, all variables will be updated at the same time.

In general, for collections that are mutable or contain mutable items, a `copy` is needed so one can change one copy without changing the other.

Note that Python creates a single new list every time you execute the [] expression. No more, no less. And Python never creates a new list if you assign a list to a variable.

```python
A = B = [] # both names will point to the same list

A = []
B = A # both names will point to the same list

A = []; B = [] # independent lists
```
Remember list slices? `L[i:j]` returns a _new_ list, containing the objects between i and j.

## The print function

Try this:

```python
name = 'Maria'
name
```
```
'Maria'
```

```python
print(name)
```
```
Maria
```

When you just type `name`, the Python interpreter responds with the string *representation* of the variable 'name', which is the letters M-a-r-i-a, surrounded by single quotes, ''. When you say `print(name)`, Python will "print" the contents of the variable to the screen, without the quotes, which is neater.

As we'll see later, `print()` is also useful when we want to print things from inside functions, or when we want to print things on multiple lines.



> ## Who's who in the memory
>
>You can use the `whos` command at any time to see what variables you have created and what modules you have loaded into the computers memory. As this is an IPython command, it will only work if you are in an IPython terminal or the Jupyter Notebook.
>
>```python
>whos
>```
>```
>Variable    Type       Data/Info
>--------------------------------
>weight_kg   float      100.0
>weight_lb   float      126.5
>```

<!--sec data-title="Challenge 2" data-id="challenge" data-show=true ces-->

Explain what the overall effect of this code is:

```python
left = 'L'
right = 'R'
temp = left
left = right
right = temp
```

Compare it to:

```python
left, right = right, left
```
Do they always do the same thing?
Which do you find easier to read?

<!--endsec-->



> ## The dark art of variable Names:
>Python has basically only three rules about naming variables: 

>* names you define must start with a letter (a-z,A-Z) or underscore (_) and can be followed by any number of letters, >digits (0-9), or underscores
>* names you define cannot be the same as any of Python's reserved words (see handout)
>* names are case-sensitive: 'YOU', 'you', 'You', and 'yOu' are all different names in Python
>Note that '-', '+', '*', and '/' are used by Python for defining operations on data and cannot be used in names.
