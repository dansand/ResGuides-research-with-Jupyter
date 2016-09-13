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

## Interpolation of sparse data

Generally we use interpolation when we'd like to model data _in between_ data points. The simplist type of interpolation is when our data is a function of 1 variable. This is often called _Univariate _ interpolation in Scipy. 

```python
from scipy import interpolate
%pylab inline

```

Let's go ahead and create some data:

```python
x = np.linspace(0, 4, 12)
y = np.cos(x**2/3+4)

xn = np.linspace(0, 4, 100)
y0 = np.cos(xn**2/3+4)
```

```python
f1 = interpolate.interp1d(x, y, kind='linear')
f0 = interpolate.interp1d(x, y, kind='nearest')
f2 = interpolate.interp1d(x, y, kind='quadratic')


yn0 = f0(xn)
yn1 = f1(xn)
yn2 = f2(xn)
```


## Gradients in noisy data
