# Jupyter Notebooks 2

> ## Learning Objectives
>
> *   Jupyer / IPython Magics
> *   Timing
> *   Running scripts
> *   Converting Notebooks to other formats
> *   Binder


## Magics

Jupyter has a set of predefined _magic functions_ that you can call with a command line style syntax. There are two kinds of magics, line-oriented and cell-oriented. Line magics are prefixed with the `%` character and work much like OS command-line calls: they get as an argument the rest of the line, where arguments are passed without parentheses or quotes. Cell magics are prefixed with a double `%%`, and they are functions that get as an argument not only the rest of the line, but also the lines below it in a separate argument.

    %load 

This magic loads a Python file from a filepath or URL and replaces the contents of the cell with the contents of the file.
    
    %pylab inline
    
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

## Timing code

    %timeit

The major advantage of the` %timeit` magic that you don't have to import timer.timeit, and run the code multiple times to figure out which is the better approach; %timeit will automatically calculate number of runs required for your code based on a total of 2 seconds execution window.


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

We can easily run scripts and load pieces of code into the notebook. As an example, let's save a function we wrote into a script. The  code for fibonacci function, if you recall was:

```python
def fibonacci(n):
    """
    Takes one argument `n` and returns the `n`-th Fibonacci number.
    """
    f0 = 0
    f1 = 1
    while n > 1:
        nxt = f0 + f1
        f0 = f1
        f1 = nxt
        n -= 1
    return f1
```
Try going to your jupyter _dashboard_ then select the `new` dropdown and selecting `Text File`. This will open a `plain text` file. Paste the contents of the fibonacci sequence function into the file, then save the file with a name like `fibonacci.py` (python scripts typically end with .py). Now we're ready to load that script into a Jupyter session. 

```python
%load fib.py
```

How about that? We now get the contents of the script in a cell. See how the `%load` magic is commented out with the `#` Not that the cell hasn't run yet - until we do that, the function has not been stored in memory.

Now try using a slightly different _magic_: `%run fib.py`.

What do you think happened here. 


## NbViewer, github Binder

Version control and social coding sites like GitHub make it simple to share code, and projects like the Jupyter notebook provide interactive interfaces for language-agnostic analysis. But executing that code remains a hurdle — dependencies, data, and system configuration are less portable than code, and are more difficult to specify. Binder has two primary goals: to make it easy to construct reproducible environments, even without knowledge of containerization technology; and to make these environments available for instantaneous deployment in the browser.



### More tricks

Adding Line Numbers
One of the most annoying things about the Jupyter Notebook is the lack of line numbers. This makes it very difficult to track down lines mentioned in error messages.

Typing CTRL-M L toggles line numbers in the focus cell.
