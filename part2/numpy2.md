# Numpy 2

> ## Learning Objectives
> *   Create useful numpy arrays 
> *   Perform operations on arrays of data.
> *   Higher dimensional arrays

## Creating arrays

We have see an example of creating an array from an existing data file using `np.genfromtxt()`. We start with this approach because as researchers, and often want to dive straight into our data. There are alos a number of ways to initialise new numpy arrays, for example:

* from a Python list or tuples
* using functions that are dedicated to generating numpy arrays, such as `arange`, `linspace`, etc.

```python 
import numpy as np
```

To create a new 1D  array from Python lists we can use the `np.array()` function.

```python 
v = np.array([1,2,3,4])
print(v)
```
```
[1 2 3 4]
```

A 2D array (sometimes called a matrix) can be created from a nested list:

```python 
M = np.array([[1, 2], [3, 4]])
print(M)
```
```
[[1 2]
 [3 4]]
```

Like all variables in Python, we should be interested in their type:

```python
print(type(v), type(M))
```
```
<class 'numpy.ndarray'> <class 'numpy.ndarray'>
```

When dealing with numpy arrays, we find it useful to commonly remind check that the size and shape of our arrays are as we would exect:

```python
print(v.shape, M.shape)
```
```
(4,) (2, 2)
```
```python
print(v.size, M.size)
```
```
4 4
```

So far the `numpy.ndarray` looks pretty much like a Python list (or nested list). Why not simply use Python lists for computations instead of creating a new array type? Basically, it all boils down to speed. As we will see later in this lesson, numpy arrays are good at maths, and more to the point, they are fast.


For larger arrays it is inpractical to initialize the data manually, using explicit python lists. Instead we can use one of the many _array-generating functions_ in numpy that generate arrays of different forms. 


```python
# create a vector with np.arange
x = np.arange(0, 10, 1) # arguments: start, stop, step
print(x)
```
```
[0 1 2 3 4 5 6 7 8 9]
```

```python
# create a vector with linspace, both end points ARE included
np.linspace(0, 10, 25) # arguments: start, end, number
```



```python
#Return a new array of given shape and type, 
#filled with zeros.
z = np.zeros((3,3))
```
```
[[ 0.  0.  0.]
 [ 0.  0.  0.]
 [ 0.  0.  0.]]
```

## Array manipulation

The reshape method lets you (almost) arbitrarily change the shape of an array


```python
z.reshape(9)
```

In this case, the same thing could have been better achived by using `flatten()`:

```python
z.flatten()
```





## Random numbers

The `numpy.random` contains a number functions that generate random numbers, and arrays of random numbers. 


The most common thing you'll probably want to do is to create an array of floats, of the given shape and populate it with
random samples from a uniform distribution (the range defaults to ``[0, 1)``).


```python
random = np.random.rand(3,2)
print(random)
```
We can change the interval:

```
np.random.seed(0)
b = np.random.uniform(low=-1, high=1, size=10)
print(b)
```
```
[ 0.09762701  0.43037873  0.20552675  0.08976637 -0.1526904   0.29178823
 -0.12482558  0.783546    0.92732552 -0.23311696]
```

Providing the `seed` to the random number generator ensures that the output will be the same. Th numbers are still a good approximation of a the uniform distribution, randomly sampled, but once the seed has been set, the algorithm is _not random_ . The seed need to be set before any call to the `numpy.random` module, otherwise it is reset. 

Random _integers_ from the uniform distribution: 

```python
p.random.seed(42)
i = np.random.randint(low=0,high=10, size=10)
print(i)
``` 

```
[6 3 7 4 6 9 2 6 7 4]
```

We can also create random samples from many common probability density functions. Let's, say an oil company drills 9 wild-cat oil exploration wells, each with an estimated probability of success of 0.1. All nine wells fail, the company gives up on oil and switches to it's focus to Renewable energy. What is the probability of that happening? Each Well is a success or fail outcome, which means we can model the process with a binomial distribution:  Let’s do 20,000 trials of the model, and count the number that generate zero positive results.

```python
np.random.seed(0)
print('answer is :', sum(np.random.binomial(n=9, p=0.1, size=20000) == 0)/20000.)
```

```
('answer is :', 0.39240000000000003)

```

## Fancy indexing

Fancy indexing generally refers using arrays of indices or Booleans to index another array. Imagine you wanted to sqaure only the negative values in an array:

```python
rand = np.random.RandomState(42)
A = rand.randint(-100,100, size=10)
T = A.copy() - 5
T[T<0] **= 2
print(T)
```

```
[   9   74  169 8281    1 1156   83 7225    9   16]
```

As you can see, numpy arrays can be indexed with boolean or integer arrays (masks). By default this creates _copies not views_.

##Looping through arrays

There are a number of ways of looping through numpy arrays

```python
np.random.seed(0)
arr = np.random.rand(2,2)
```


```python
for x in np.nditer(arr):
    print(x)
```

```
0.548813503927
0.715189366372
0.602763376072
0.544883182997
```



```python

for index, x in np.ndenumerate(arr):
    print(index)
    print(x)
```
```
(0, 0)
0.548813503927
(0, 1)
0.715189366372
(1, 0)
0.602763376072
(1, 1)
0.544883182997
```

Note that the indexes are returned as a `Tuple` (an immutable list). If you see Python output that looks like `(n,)`, this is the default print style of the single-element tuple.  

## Images as arrays


In order to have a more visually appealing array to work with,  let's read in an image from the Scipy sample data:

```python
from scipy import misc
face = misc.face()
print(type(face))
```

```
<type 'numpy.ndarray'>
```


```python       
plt.imshow(face)
```

It's common that libraries include a small ammount of reprentative data, for examples / demonstrations. 



<!--sec data-title="the dreaded greyscale" data-id="challenge1" data-show=true ces-->


Now we know we know a little about doing maths with arrays, we can define a function a to convert a colour (RGB) image to grayscale.
 
The equivalent Matlab function uses the following formula:

$$ gray = 0.2989 \times red + 0.5870 \times green+ 0.1140 \times blue $$
 
Write a python function that will compute the grayscale representation of our `face` array.


<!--endsec-->

<!--sec data-title="unpacking the meaning" data-id="challenge2" data-show=true ces-->


Explain the output of the following. If you're stuck,try breaking up the multitude of functions and methods used in the third line.  

```python 
np.random.seed(0)  # seed for reproducibility
z = 0.5
m = Z[np.abs(np.random.uniform(0,1,10) - z).argmin()]
print(m)
```

<!--endsec-->


<!--sec data-title="checkerboard" data-id="challenge3" data-show=true ces-->

Create an 8x8 matrix and fill it with a checkerboard pattern.

<!--endsec-->
