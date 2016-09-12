# Jupyter Notebooks 1

> ## Learning Objectives
>
> *   Explain what the Jupyter Notebook environment is.
> *   Creation / execution of code cells.
> *   Markdown and markdown cells
> *   Shortcuts


## What are they?

Notebooks are documents produced by the Jupyter Notebook App which contain both computer code (e.g. python) and rich text elements (paragraph, equations, figures, links, etc...). Notebook documents are both human-readable documents containing the analysis description and the results (figures, tables, etc..) as well as executable documents which can be run to perform data analysis.

The Jupyter Notebook App is a web application that allows you to create and share documents that contain live code, equations, visualizations and explanatory text.

_How will the children of the future learn about science? How will the scientists of the future expand our thinking? I think the answer is Jupyter Notebooks._ (Safia Abdalla)

Jupyter Notebooks were formally called ipython notebooks...hence the .ipynb file extension legacy

## The notebook dashboard

The Notebook Dashboard is the component which is shown first when launching Jupyter Notebook App. The Notebook Dashboard is mainly used to open notebook documents, and to manage the running kernels (visualize and shutdown).

Make sure you have a Notebook. If you don't have iPython/Jupyter on your computer, you can run a temporary notebook here:
[Tempnb](https://tmpnb.org/). You should be able to follow much of this course using [Tempnb](https://tmpnb.org/), the only restriction being you can't download the example data sets. 


## Markdown

Explanatory text can be integrating with the Jupyter Notebook using a simple formatting schema called _Markdown_. See the link for a basic description.
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

## Keyboard Shortcuts

### Command mode vs. Edit mode

But first...something key to be aware of: Jupyter Notebooks have two different keyboard input modes:

1. **Command mode** - binds the keyboard to notebook level actions. Indicated by a grey cell border with a blue left margin. Press `esc` to enable.
2. **Edit mode** - when you're typing in a cell. Indicated by a green cell border


### Command Mode

- `shift` + `enter` run cell, select below
- `ctrl` + `enter` run cell
- `option` + `enter` run cell, insert below
- `A` insert cell above
- `B` insert cell below
- `C` copy cell
- `V` paste cell
- `D` , `D` delete selected cell
- `shift` + `M` merge selected cells, or current cell with cell below if only one cell selected
- `Y` change cell to `code` mode
- `M` change cell to `markdown` mode (good for documentation)


### Edit Mode


- `cmd` + `/` toggle comment lines
- `tab` code completion or indent

## Command Palette

`cmd` + `shift` + `p`

Want quick access to all the commands in Jupyter Notebooks? Open the command palette with `cmd` + `shift` + `p` and you'll quickly be able to search all the commands!

__The point is not remember all these, but to see that the Notebooks are equpied with all kinds of shortcuts to more efficiently produce content__

## Other Languages

Not just Python! The Notebook has support for over 40 programming languages, including those popular in Data Science such as Python, R, Julia and Scala.


## Literate programming & Reprodicible research 

Literate programming is an approach to programming introduced by Donald Knuth in which a program is given as an explanation of the program logic in a natural language, such as English, interspersed with snippets of macros and traditional source code, from which a compilable source code can be generated.

