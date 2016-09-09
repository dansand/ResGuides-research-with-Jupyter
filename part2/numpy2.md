# Numpy 2

> ## Learning Objectives
> *   Create useful numpy arrays 
> *   Perform operations on arrays of data.
> *   Higher dimensional arrays

## Creating arrays

We have see an example of creating an array from an existing data file using `np.genfromtxt()`. We start with this approach because as researchers, and often want to dive straigt into our data.There are a number of more formulaic ways to initialise new numpy arrays, for example:

* from a Python list or tuples
* using functions that are dedicated to generating numpy arrays, such as `arange`, `linspace`, etc.

To create a new 1D  array (sometimes called a vector) from Python lists we can use the np.array function.

```python 
v = array([1,2,3,4])
print(v)
```
```
[1 2 3 4]
```

A 2D array (sometimes called a matrix) can be created from a nested list:

```python 
M = array([[1, 2], [3, 4]])
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

And as numpt arrays, we should be concerned about their size and shape:

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
linspace(0, 10, 25) # arguments: start, end, number
```

Let's plot some point generated using `np.linspace`

```python
x = np.linspace(0, 3, 20)
y = np.linspace(0, 9, 20)
plt.plot(x, y)       # line plot
plt.plot(x, y, 'o')  # dot plot
plt.show() 
```


```python
x, y = np.mgrid[0:3, 0:3] # similar to meshgrid in MATLAB
print(x), print(y)
```
```
[[0 0 0]
 [1 1 1]
 [2 2 2]]
[[0 1 2]
 [0 1 2]
 [0 1 2]]
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

```python
# Create an array of the given shape /
# and fill with random samples 
# from a uniform distribution over [0, 1).
random = np.random.rand(3,2)
print(random
```
```
[[ 0.95642119  0.82504981]
 [ 0.01412624  0.00413452]
 [ 0.37054704  0.55093531]]
```
(For example)

In order to have a more visually appealing array to work with,  let's read in an image from the Scipy sample data:

```python
from scipy import misc
face = misc.face()
```

```python       
plt.imshow(f)
```






##Looping through arrays

There are a number of ways of looping through `np.arrays`.

```python
#for x in np.nditer(data):
#    print(x)
```

```python

for index, x in np.ndenumerate(data):
    print(index, x)
```



> ##_challenge:_  dreaded greyscale
>
> Now we know we know a little about doing maths with arrays, we can define a function a to convert a colour (RGB) image to grayscale.
> 
> The equivalent Matlab function uses the following formula:
>$$gray = 0.2989 \times red + 0.5870 \times green+ 0.1140 \times blue$$
> 
> 
>Write a python function that will compute the grayscale representation of our `face` array.

>  ##_challenge:_  Interpret
> Explain the output of the following
> ```python
> Z = np.random.uniform(0,1,10)
> z = 0.5
> m = Z.flat[np.abs(Z - z).argmin()]
> print(m)
> ```

> ## _challenge:_ Checkerboard
>Create an 8x8 matrix and fill it with a checkerboard pattern

> ## _challenge:_ Normalise 
Normalise a 5x5 random matrix 


