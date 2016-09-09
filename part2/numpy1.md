#Numpy 1

> ## Learning Objectives
>
> *   Load a Python library and use the things it contains.
> *   Read tabular data from a file into a program.
> *   Select individual values and subsections from data.


We are going to hit the ground running and import some numerical data. In this case, we have a csv file containing data form from the Nasdaq (to be precise, the Nasdaq Composite index). This tutorial assumes the data is located in the followinf _relative path_: `data/nasdaq.csv`.


In order to load our data, we will use a function from library NumPy. In general you should use this library if you want to do analysis things numbers (Numpy is no good with textual data).

We can load NumPy using:

```python
import numpy as np
```

Importing a library is like getting a piece of lab equipment out of a storage locker and setting it up on the bench. Libraries provide additional functionality to the basic Python package, much like a new piece of equipment adds functionality to a lab space. Once you've loaded the library, we can ask the library to read our data file for us:

```python
np.loadtxt('data/nasdaq.csv', delimiter=',', skiprows=1, usecols=(4,5))
```
```
array([ 5227.209961,  5213.220215,  5222.990234, ...,   100.760002,
         100.839996,   100.      ])
```

The expression `np.loadtxt` is a [function call](reference.html#function-call) that asks Python to run the function `loadtxt` that belongs to the `numpy` library.

This dotted notation is used everywhere in Python to refer to the parts of things as `thing.component`.

`np.loadtxt` has a number of _parameters_. Most importantly, the the name of the file we want to read, and the _delimiter_ that separates values on a line. These both need to be character strings (or _strings_, so we put them in quotes.

By default, only a few rows and columns are shown (with `...` to omit elements when displaying big arrays). To save space, Python displays numbers as `1.` instead of `1.0` when there's nothing interesting after the decimal point.

Our call to `numpy.loadtxt` read our file, but didn't save the data in memory. To do that, we need to _assign_ the array to a _variable_

Just as we can assign a single value to a integer,or list, or string (native data types) we can also assign an numpy array 
to a variable using the same syntax.  Let's re-run `numpy.loadtxt` and save its result:

```python
filepath = 'data/nasdaq.csv'
data = np.loadtxt(filepath, delimiter=',', skiprows=1, usecols=(4,5))

```

We also put the file path into a variable called`filepath`, which can help make the call to `np.loadtxt` a bit simpler.

Also, notice we supplied a function argument `skiprows`, and `usecols`. Depending on you file, these paramters might be useful, or critical, or both. But this is a bit of an aside, we'll cover this in more detail in the I/O section. 



##Accessing our data

Now that our data is in memory,
we can start doing things with it.
First,
let's ask what _type_ of thing `data` refers to:

```python
print(type(data))
```

```
<class 'numpy.ndarray'>
```

The output tells us that `data` currently refers to an N-dimensional array created by the NumPy library. These data correspond to historical temperature records from Europe. The rows are the years and the columns are the seasons.

We can see what its [shape](reference.html#shape) is like this:

```python
print(data.shape)
```

```
(11495, 2)
```

This tells us that `data` has 11495 rows, and 2 columns (it is 2-dimensional). When we created the variable `data` to store our past climate data, we didn't just create the array, we also created information about the array, called _attributes_. This extra information describes `data` in the same way an adjective describes a noun. `data.shape` is an attribute  of `data` which described the dimensions of `data`. We use the same dotted notation for the attributes of variables that we use for the functions in libraries because they have the same part-and-whole relationship.

If we want to get a single number from the array,
we must provide an [index](reference.html#index) in square bracket, similar to how we have worked with lists:

```Python
print('first value in data:', data[0, 0])
```

```
('first value in data:', 5227.2099609999996)

```

```python
print('some random value in data:', data[250, 0])
```python

```python
('some random value in data:', 4683.919922)
```python

Hopefully, `data[0,0]` reminds you a bit of the indexing scheme we used for lists.

As a result, if we have an MxN array in Python, its indices go from 0 to M-1 on the first axis and 0 to N-1 on the second. It takes a bit of getting used to, but one way to remember the rule is that the index is how many steps we have to take from the start to get the item we want.


An index like `data[250, 0]` selects a single element of an array, but we can select whole sections as well. For example, we can select the first ten days (columns) of values for the first four patients (rows) like this:

```python
print(data[0:10, 0:2])
```

```
[[  5.22720996e+03   1.59252000e+09]
 [  5.21322022e+03   1.76177000e+09]
 [  5.22299023e+03   1.56102000e+09]
 [  5.23233008e+03   1.41664000e+09]
 [  5.21891992e+03   1.59106000e+09]
 [  5.21220020e+03   1.51189000e+09]
 [  5.21768994e+03   1.71478000e+09]
 [  5.26008008e+03   1.54705000e+09]
 [  5.24460010e+03   1.56021000e+09]
 [  5.23837988e+03   1.63274000e+09]]
```

The _slice_ `0:10` means, "Start at index 0 and go up to, but not including, index 10." Again, the up-to-but-not-including takes a bit of getting used to, but the rule is that the difference between the upper and lower bounds is the number of values in the slice.

We don't have to start slices at 0:

```python
print(data[5:10, 0:2])
```
```python
[[  5.21220020e+03   1.51189000e+09]
 [  5.21768994e+03   1.71478000e+09]
 [  5.26008008e+03   1.54705000e+09]
 [  5.24460010e+03   1.56021000e+09]
 [  5.23837988e+03   1.63274000e+09]]
```

We also don't have to include the upper and lower bound on the slice. If we don't include the lower bound, Python uses 0 by default; if we don't include the upper, the slice runs to the end of the axis, and if we don't include either (i.e., if we just use ':' on its own),
the slice includes everything:

```python
small = data[:5, 0:]
print('small is:')
print(small)
```
```
[[  5.22720996e+03   1.59252000e+09]
 [  5.21322022e+03   1.76177000e+09]
 [  5.22299023e+03   1.56102000e+09]
 [  5.23233008e+03   1.41664000e+09]
 [  5.21891992e+03   1.59106000e+09]]
``` 
 
 ## Cleaning our data
 
 At this point we should think a little bit about what our numpy array actually contains. Fistly, why all that scienctific notation? When our array contains both large and small values, numpy defaults to printing this way. In this case, there si sufficient variation in the magnitude of our values to have triggered this prinitng option,
 
 If you'd like to learn about overidding this behavior, have a search for examples of setting `np.set_printoptions` on [](http://stackoverflow.com/).


Okay, what about the first column? 

```print
print(data[0:5,0])
```
```
[ 5227.209961  5213.220215  5222.990234  5232.330078  5218.919922]
```
These values represent the daily closing price for the Nasdaq composite index. One thing you may notice is that these values look like floats (floating point numbers). Unlike lists, Numpy arrays can only contain numbers. Even more restrictive, each instance of an array can only have ony type or number...e.g. float, int, complex. To find out which type of data out array contains, we can write
 
```python
data.dtype
```
```
dtype('float64')
```
We cannot change the data type of a sub-array, only the entire array.

```python
data[0,0] = int(1500)
print(data[0,0])
``` 
```
1500.0
```
As this code block shows, numpy will always coerce _numbers_ into the correct (i.e current) data type. Strings and other non-numeric objects, however, will fail:

```python
data[0,0] = "hello"
```
```
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-12-a09d72434238> in <module>()
----> 1 data[0,0] = "hello"
```



## Plotting our data

Let's have a quick look look at our data:

```python
%pylab inline
plt.plot(data[:,0])
```

plot here...

That was pretty easy huh!


## Shell commands in the Jupyter notebook


```python
!head -2 $filepath
```
```
Date,Open,High,Low,Close,Volume,Adj Close
2016-09-02,5249.660156,5263.390137,5231.02002,5249.899902,1474200000,5249.899902

```

## Something useful


 
