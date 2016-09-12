#Python libraries / modules

> ## Learning Objectives
>
> *  What are libraries?
> *  How to use them
> *  Where to get them

## Libraries / packages modules

* A package is a collection of python modules under a common namespace. In practice one is created by placing multiple python modules in a directory with a special __init__.py module (file).

* A module is a single file of python code that is meant to be imported. This is a bit of a simplification since in practice quite a few modules detect when they are run as script and do something special in that case. Simply put, a module in python is a .py file that defines one or more function/classes which you intend to reuse in different codes of your program.
* Unlike C or C++, the term library does not have any specific contextual meaning in p\Python. When used in Python, a library is used loosely to describe a collection of the core modules.

```python
from mypackage.mymodule import myclass
```

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

For convenience, Python comes with a program called pip (a recursive acronym meaning "pip installs packages"), which will automatically fetch packages released and listed on PyPI (if you use Python version 2, pip must be installed separately). Running either if these from the command line (assuming pip and anaconda are installed on your system), will install the bokeh plotting library:

```
pip install bokeh
```

```
conda install bokeh
```


## Summary

Just like functions are reusable parts of programs, modules are reusable programs.
