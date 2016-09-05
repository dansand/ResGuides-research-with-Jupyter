
# Lists

> ## Learning Objectives
>
> *   Explain what a list is.
> *   Create a variable to store a list.
> *   Create and index lists of simple values.
> *   List slicing.

##Creating lists

A list is a way to store many values. We create a list by putting values inside square brackets:

```python
[1, 3, 5, 7]
```
```
[1, 3, 5, 7]
```

The list was evaluated by Python (and returned to us) but Python didn’t save the data in memory. To do that, we need to assign the list to a variable. A variable is just a name for a value, such as x, current_temperature, or subject_id. Python’s variables must begin with a letter and are case sensitive. We can create a new variable by assigning a value to it using =. As an illustration, let’s step back and instead of considering a table of data, consider the simplest “collection” of data, a single value. The line below assigns the value 55 to a variable weight_kg:

```python
weight_kg = 55
```

Let's _assign_ that list to a variable now:

```python
odds = [1, 3, 5, 7]
print('odds are:', odds)
```
```
odds are: [1, 3, 5, 7]
```

##Indexing a list

An index is the number that says where in a list an item occurs.We select individual elements from lists by _indexing_ them:

```python
print('first and last:', odds[0], odds[-1])
```
```
first and last: 1 7
```

Programming languages like Fortran and MATLAB start counting at 1, because that's what human beings have done for thousands of years.Languages in the C family (including C++, Java, Perl, and Python) count from 0 because that's simpler for computers to do.


There is one important difference between lists and strings:
we can change the values in a list,
but we cannot change the characters in a string.
For example:

```python
names = ['Newton', 'Darwing', 'Turing'] # typo in Darwin's name
print('names is originally:', names)
names[1] = 'Darwin' # correct the name
print('final value of names:', names)
```
```
names is originally: ['Newton', 'Darwing', 'Turing']
final value of names: ['Newton', 'Darwin', 'Turing']
```

works, but:

```python
name = 'Bell'
name[0] = 'b'
```
```
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-8-220df48aeb2e> in <module>()
      1 name = 'Bell'
----> 2 name[0] = 'b'

TypeError: 'str' object does not support item assignment
```

does not.

> ## Ch-Ch-Ch-Changes
>
> Data which can be modified in place is called [mutable](reference.html#mutable),
> while data which cannot be modified is called [immutable](reference.html#immutable).
> Strings and numbers are immutable. This does not mean that variables with string or number values are constants,
> but when we want to change the value of a string or number variable, we can only replace the old value
> with a completely new value.
>
> Lists and arrays, on the other hand, are mutable: we can modify them after they have been created. We can
> change individual elements, append new elements, or reorder the whole list.  For some operations, like
> sorting, we can choose whether to use a function that modifies the data in place or a function that returns a
> modified copy and leaves the original unchanged.


##Methods

A list is an example of usage of objects and classes. When we use a variable i and assign a value to it, say integer 5 to it, you can think of it as creating an object (i.e. instance) i of class (i.e. type) int. In fact, you can read help(int) to understand this better.
A class can also have methods i.e. functions defined for use with respect to that class only. You can use these pieces of functionality only when you have an object of that class. For example, Python provides an append method for the list class which allows you to add an item to the end of the list. For example, `mylist.append('an item')` will add that string to the list `mylist`. Note the use of dotted notation for accessing methods of the objects.

There are many ways to change the contents of lists besides assigning new values to
individual elements:

~~~ {.python}
odds.append(11)
print('odds after adding a value:', odds)
~~~
~~~ {.output}
odds after adding a value: [1, 3, 5, 7, 11]
~~~

~~~ {.python}
del odds[0]
print('odds after removing the first element:', odds)
~~~
~~~ {.output}
odds after removing the first element: [3, 5, 7, 11]
~~~

~~~ {.python}
odds.reverse()
print('odds after reversing:', odds)
~~~
~~~ {.output}
odds after reversing: [11, 7, 5, 3]
~~~

While modifying in place, it is useful to remember that Python treats lists in a slightly counterintuitive way.

If we make a list and (attempt to) copy it then modify in place, we can cause all sorts of trouble:

~~~ {.python}
odds = [1, 3, 5, 7]
primes = odds
primes += [2]
print('primes:', primes)
print('odds:', odds)
~~~
~~~ {.output}
primes: [1, 3, 5, 7, 2]
odds: [1, 3, 5, 7, 2]
~~~

This is because Python stores a list in memory, and then can use multiple names to refer to the same list.
If all we want to do is copy a (simple) list, we can use the `list` function, so we do not modify a list we did not mean to:

~~~ {.python}
odds = [1, 3, 5, 7]
primes = list(odds)
primes += [2]
print('primes:', primes)
print('odds:', odds)
~~~
~~~ {.output}
primes: [1, 3, 5, 7, 2]
odds: [1, 3, 5, 7]
~~~

This is different from how variables worked in lesson 1, and more similar to how a spreadsheet works.

##Slicing

lists, (like a variety of python data structures), also have a slicing operation which allows us to retrieve a slice of the sequence i.e. a part of the sequence.


```python
odds = [1, 3, 5, 7]
print('Item 1 to 3 is', odds[1:3])
print('Item 2 to end is', odds[2:])
print('Item 1 to -1 is', odds[1:-1])
print('Item start to end is', odds[:])
```
```
Item 1 to 3 is [3, 5]
Item 2 to end is [5, 7]
Item 1 to -1 is [3, 5]
Item start to end is [1, 3, 5, 7]
```

##Anything goes

Lists are just one example of a Python _container_. Lists have certain inalienable rights, we've sen that the items of a list can be changed at will. Lists can also contain items of different __types_. Together these properties make lists very flexible. Sometimes this flexibility is undesirable - later we will encounter containers that are more restrictive in how we can interact with them.


<!--sec data-title="Challenge 1" data-id="challenge" data-show=true ces-->

We've now encountered lists and strings as two fundamental python containers. Explain what the overall effect of this code is:

```python
list1 = ["I", "am", "becoming", "a", "programmer"]
message = "\n".join(list1)
print(message)
```

_hint, try running_
```
help(message.join)
```

<!--endsec-->






