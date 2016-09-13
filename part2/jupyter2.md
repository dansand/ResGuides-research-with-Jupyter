# Jupyter Notebooks 2

> ## Learning Objectives
>
> *   Jupyer / IPython Magics
> *   Timing
> *   Running scripts
> *   Converting Notebooks to other formats
> *   Binder


## Magics

    %load 

This magic loads a Python file from a filepath or URL and replaces the contents of the cell with the contents of the file.
    
    %matplotlib inline
    
This magic places matplotlib plots inline instead of opening a new window.

    %%writefile

This magic writes the contents of a cell to a file.

    %pprint

This magic toggles pretty print on/off

    %reset

This magic resets the namespace by removing all names defined by the user, if called without arguments.

    %timeit

This magic times the execution of a Python statement or expression. The CPU and clock times are printed.

    %%html

Render the cell as a block of HTML

    %%latex

Render the cell as a block of latex

## Timing code

    %timeit

The major advantage of the` %timeit` magig that you don't have to import timer.timeit, and run the code multiple times to figure out which is the better approach; %timeit will automatically calculate number of runs required for your code based on a total of 2 seconds execution window.


```python
%timeit sum(range(100))
```
```
The slowest run took 7.94 times longer than the fastest. This could mean that an intermediate result is being cached.
10000 loops, best of 3: 28.2 µs per loop
```

```python

%%time
total = 0
for i in range(1000):
    for j in range(1000):
        total += i * (-1) ** j
```

```
CPU times: user 1.1 s, sys: 2.88 ms, total: 1.1 s
Wall time: 1.1 s
```

## Converting notebooks to scripts (and other formats)

    jupyter nbconvert --to script name_of_notebook.ipynb



## What about scripts?



## Binder

Version control and social coding sites like GitHub make it simple to share code, and projects like the Jupyter notebook provide interactive interfaces for language-agnostic analysis. But executing that code remains a hurdle — dependencies, data, and system configuration are less portable than code, and are more difficult to specify. Binder has two primary goals: to make it easy to construct reproducible environments, even without knowledge of containerization technology; and to make these environments available for instantaneous deployment in the browser.



### More tricks

Adding Line Numbers
One of the most annoying things about the Jupyter Notebook is the lack of line numbers. This makes it very difficult to track down lines mentioned in error messages.

Typing CTRL-M L toggles line numbers in the focus cell.
