# Math

> ## Learning Objectives
>
> *   Basic functions of the math library
> *   In place operators
> *   array math with numpy


##The math library


The math library is part of the Standard library, and provides many mathematical _functions_ that extend the basic _operators_ we saw previously.

We need to import the math library before we can use it:

```python
import math
print("sin pi/2:", math.sin(math.pi/2))
```

```
('sin pi/2:', 1.0)
```

## In place operators. 

A Python sytax that can be a little confusing to begin with is the use of _in-place-operators_. Compare:

```python
a = 2.
a = a +  2
print(a)
```

```
4.0
```

```python
a = 2.
a += 2
print(a)
```

```
4.0
```

This will work for all mathematical operators. The syntax It also extends to other data types, specifically, numpy arrays:

```python
a = np.array([1, 2, 3], float)
b = a
print(a is b)
a += 4
print(a is b)
print(a, b)
```
```
True
True
(array([ 5.,  6.,  7.]), array([ 5.,  6.,  7.]))
```


The behaviour is different here than if we had used the _non-in-place_ operation:

```python
a = np.array([1, 2, 3], float)
b = a
print(a is b)
a = a + 4
print(a is b)
print(a, b)
```

```
True
False
(array([ 5.,  6.,  7.]), array([ 1.,  2.,  3.]))
```

## Math with arrays

We cannot apply `maths` library functions, element wise, to lists or numpy arrays:

```python
a = np.array([1, 2, 3], float)
print(math.exp(a))
```

```
TypeError                                 Traceback (most recent call last)
<ipython-input-389-4f48d5ba7274> in <module>()
      1 a = np.array([1, 2, 3], float)
----> 2 math.exp(a)

TypeError: only length-1 arrays can be converted to Python scalars
```

Instead, we use the same mathematical functions directly from the numpy library:

```python
a = np.array([1, 2, 3], float)
print(numpy.exp(a))
```

```
[  2.71828183   7.3890561   20.08553692]
```


