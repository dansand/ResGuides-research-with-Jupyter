
# Lists

> ## Learning Objectives
>
> *   Explain what a list is.
> *   Create a variable to store a list.
> *   Create and index lists of simple values.
> *   List slicing.

##The listmakers

 A list is a way to store many values. As long as the values are objects recognisable to Python, they can go in a list. We create a list simply by putting values inside square brackets:

```python
[1, 3, 5, 7]
```
```
[1, 3, 5, 7]
```

The list was evaluated by Python (and returned to us) but Python didn’t save the data in memory. To do that, we need to assign the list to a variable. A variable is just a name for a value, such as `x`, `current_temperature`, or `subject_id`. Python’s variables must begin with a letter and are case sensitive. We can create a new variable by assigning a value to it using `=`

```python
weight_kg = 55
```

Okay, so just to be clear, `=` is the assignment operator in Python; it binds a data object to a variable name, so that we can easilt refer to that object. A different operator, which we will see later, is used for equality comparison (`==`).

Let's _assign_ our list to a variable:

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

Notice how our variable now stands for the data object, in this case a list. This is the beatiful simplicity of programming - now we can deal with and act on a simple, easy-to-rememeber variable, even if _points_ to a large, complex data object.

Note that programming languages in the C family (including C++, Java, Perl, and Python) count from 0 (because that's simpler for computers to do).

There is one important difference between lists and strings: we can change the values in a list, but we cannot change the characters in a string. For example:

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

A list is an _ordered_ sequence of items. Having order means we can index with numbers. Not all Python data types (containers) have this kind of order.  


> ## Ch-Ch-Ch-Changes
>
> Data which can be modified in place is called _mutable_
> while data which cannot be modified is called _immutable_
> Strings and numbers are immutable. This does not mean that variables with string or number values are constants,
> but when we want to change the value of a string or number variable, we can only replace the old value
> with a completely new value.
>
> Lists and arrays, on the other hand, are mutable: we can modify them after they have been created. We can
> change individual elements, append new elements, or reorder the whole list.  For some operations, like
> sorting, we can choose whether to use a function that modifies the data in place or a function that returns a
> modified copy and leaves the original unchanged.


##Methods

A list is an example of usage of _objects_ and _classes_. When we use a variable `i` and assign a value to it, say integer `5` to it, you can think of it as creating an object (i.e. instance) `i` of class (i.e. type) _int_.

As we touched on briefly in the first lessons, classes can also have methods i.e. functions defined for use with respect to that class only. You can use these pieces of functionality only when you have an object of that class. For example, Python provides an append method for the list class which allows you to add an item to the end of the list. For example, `mylist.append('an item')` will add that string to the list `mylist`. Note the use of dotted notation for accessing methods of the objects.

There are many ways to change the contents of lists besides assigning new values to individual elements:

```python
odds.append(11)
print('odds after adding a value:', odds)
```

```
odds after adding a value: [1, 3, 5, 7, 11]
```

```python
del odds[0]
print('odds after removing the first element:', odds)
```

```
odds after removing the first element: [3, 5, 7, 11]
```

```python
odds.reverse()
print('odds after reversing:', odds)
```

```
odds after reversing: [11, 7, 5, 3]
```


##Slicing

Lists, (like a variety of python data structures), also have a slicing operation which allows us to retrieve a _slice_ of the sequence (i.e. a part of the sequence).


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

Lists are just one example of a Python _container_ or _collection_. Lists have certain properties, and one we've just seen is that the items of a list can be changed at any time. We can reach in and delete, or update any item in the list. Lists can also contain items of different _types_. Together these properties make lists very flexible. Sometimes this flexibility is undesirable - later we will encounter containers that are more restrictive in how we can interact with them.

## Challenges


<!--sec data-title="Challenge 1" data-id="challenge" data-show=true ces-->

So far, most of the elements that we have added to our collections have been string, float, or integer data types. However, the elements of a collections can be collections themselves. Indeed, we can include any data type inside a tuple or a list or even a set. This process is called nesting and it is a bit like Russian dolls.

```python
pets = ['dogs', 'cats', 'fish']
print( pets )
pets.pop(0)   # Get rid of dogs
dog_breeds = ['bulldog', 'terrier', 'greyhound']
pets.append(dog_breeds)  # append list of dog breeds available
pets
```

With your neighbour, work out how to index this list, so you return the `greyound` string.

<!--endsec-->
