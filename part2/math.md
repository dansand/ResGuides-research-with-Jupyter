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

This will work for all mathematical operators.

