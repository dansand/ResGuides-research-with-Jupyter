# plotting

> ## Learning Objectives
> *  Plot data with matplotlib and seaborn 
> *  Matplotlib is Object Oriented
> *  Look ahead: Intercative visualisation with IPython Widgets & Bokeh


##Matplotlib and notebooks


Matplotlib is an excellent 2D and 3D graphics library for generating scientific figures. Some of the many advantages of this library include:
* Easy to get started
* Support for $\LaTeX$ formatted labels and texts
* Great control of every element in a figure, including figure size and DPI.
* High-quality output in many formats, including PNG, PDF, SVG, EPS, and PGF.

In the jupyter notebook environment, there is a single command that imports both matplotlib, and configures the notebook so that figure show up in the notebook (rather than in a seperate viewer window).

```python
%pylab inline
```

For consistentcy, note that this Notebook _magic command_ is actually running:

```python
from matplotlib import pyplot as plt
import numpy as np
```

We prefer the explicit imports of these libraries in addition to ` %pylab inline`.

##Object oriented programming

The main idea with object-oriented programming is to have objects that one can apply functions and actions on, and no object or program states should be global (such as the MATLAB-like API). The real advantage of this approach becomes apparent when more than one figure is created, or when a figure contains more than one subplot. 

Let's start out by creating some toy data:

```python
x = np.linspace(0, 5, 10)
y = x ** 2
```

To use the object-oriented API we start out we store a reference to the newly created figure instance in the fig variable, and from it we create a new axis instance axes using the add_axes method in the Figure class instance fig:

```

fig = plt.figure()
axes = fig.add_axes([0.1, 0.1, 0.8, 0.8]) # left, bottom, width, height (range 0 to 1)
axes.plot(x, y, 'r')
axes.set_xlabel('x')
axes.set_ylabel('y')
axes.set_title('title')
```
