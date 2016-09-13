# The Scipy library

> ## Learning Objectives
> *  Introduce the diverse scipy tools
> * Interpolation
> * Scikit Image


SciPy is a collection of scientific functionality that is built on NumPy. The package began as a set of Python wrappers to well-known Fortran libraries for numerical computing, and has grown from there. The package is arranged as a set of submodules, each implementing some class of numerical algorithms. Here is an incomplete sample of some of the more important ones for data science:

* scipy.fftpack: Fast Fourier transforms
* scipy.integrate: Numerical integration
* scipy.interpolate: Numerical interpolation
* scipy.linalg: Linear algebra routines
* scipy.optimize: Numerical optimization of functions
* scipy.sparse: Sparse matrix storage and linear algebra
* scipy.stats: Statistical analysis routines

## Interpolation and gradients

Let's once again grab our Nasdaq data

```python
import numpy as np
import scipy as sp
```

```python
filename = 'data/nasdaq.csv'
data = np.loadtxt(filename, delimiter=',', skiprows=1,usecols=(4,5))
close = data[::-1, 0].copy()
```
