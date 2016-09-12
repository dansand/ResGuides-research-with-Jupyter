#Python libraries / modules

> ## Learning Objectives
>
> *  What are libraries?
> *  How to use them
> *  Where to get them

## Standard Library

Up until now, we've mainly been uing the Python Standard library. The library contains built-in modules (written in C) that provide access to system functionality such as file I/O that would otherwise be inaccessible to Python programmers, as well as modules written in Python that provide standardized solutions for many problems that occur in everyday programming.

All modules from Python's Standard Library can be imported with the import statement, and then explored using the `help` function. Here is an extremely incomplete list of some of the modules you might wish to explore and learn about:
 
* The `os` module provides functions for interacting with the operating system
* The `glob` module provides a function for making file lists from directory wildcard searches
* The `math` module gives access to the underlying C library functions for floating point math:
* The `datetime` module supplies classes for manipulating dates and times in both simple and complex ways

glob example here..


##importing a library

```python
import math
help(math)
```


```
Help on module math:

NAME
    math

DESCRIPTION
    This module is always available.  It provides access to the
    mathematical functions defined by the C standard.

FUNCTIONS
    acos(...)
        acos(x)

        Return the arc cosine (measured in radians) of x.

    acosh(...)
        acosh(x)

        Return the inverse hyperbolic cosine of x.

...

```

Sometimes rather than importing the module namespace, you would just like to import a few particular items from the module. This can be done with the "from ... import ..." pattern. For example, we can import just the cos function and the pi constant from the math module:

```python
from math import cos, pi
cos(pi)
```

## Third party modules

In addition to the standard library, there is a growing collection of several thousand components (from individual programs and modules to packages and entire application development frameworks), available from the Python Package Index (PIP), or Conda.


## Summary

Just like functions are reusable parts of programs, modules are reusable programs.
