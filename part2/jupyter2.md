# Jupyter Notebooks 2

> ## Learning Objectives
>
> *   Jupyer / IPython Magics
> *   Running scripts
> *  Inline plotting with `%pylab inline`
> *  converting Notebooks to other formats
> *   Converting to scripts
> *   Binder


###Magics

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

### Converting notebooks to scripts (and other formats)

    jupyter nbconvert --to script name_of_notebook.ipynb



### What about scripts?



### Binder

Version control and social coding sites like GitHub make it simple to share code, and projects like the Jupyter notebook provide interactive interfaces for language-agnostic analysis. But executing that code remains a hurdle — dependencies, data, and system configuration are less portable than code, and are more difficult to specify. Binder has two primary goals: to make it easy to construct reproducible environments, even without knowledge of containerization technology; and to make these environments available for instantaneous deployment in the browser.



### More tricks

Adding Line Numbers
One of the most annoying things about the Jupyter Notebook is the lack of line numbers. This makes it very difficult to track down lines mentioned in error messages.

Typing CTRL-M L toggles line numbers in the focus cell.
