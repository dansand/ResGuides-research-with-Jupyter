# Conditions

> ## Learning Objectives
>
> *   Explain the similarities and differences between tuples and lists.
> *   Write conditional statements including `if`, `elif`, and `else` branches.
> *   Correctly evaluate expressions containing `and` and `or`.


## Comparing things

In the first lesson, we saw some mathematical operators. Python is also equipped with comparison operators. All comparison operators return `True` or `False`. Note the capitalization of these names.

A big part of programming includes comparing things. What's the easiest thing to compare? Numbers, of course. Let's see how that works:

```python
print(5 > 2)
print(3 < 1)
print(5 > 2 * 2)
print(1 == 1)
print(5 != 2)
```    
```
True
False
True
True
True
```

We gave Python some numbers to compare. As you can see, Python can compare not only numbers, but it can also compare method results. Nice, huh?

Give Python two more tasks:

```python
print(6 >= 12 / 2)
print(3 <= 2)
```
```    
True
False
```

`>` and `<` are easy, but what do `>=` and `<=` mean? Read them like this:

- x `>` y means: x is greater than y
- x `<` y means: x is less than y
- x `<=` y means: x is less than or equal to y
- x `>=` y means: x is greater than or equal to y



## Control flow

We can ask Python to take different actions, depending on a condition, with an `if` statement:

```python
num = 37
if num > 100:
    print('greater')
else:
    print('not greater')
print('done')
```
```
not greater
done
```

The second line of this code uses the keyword `if` to tell Python that we want to make a choice.
If the test that follows the `if` statement is true,
the body of the `if`
(i.e., the lines indented underneath it) are executed.
If the test is false,
the body of the `else` is executed instead.
Only one or the other is ever executed:

<!--
![Executing a Conditional](fig/python-flowchart-conditional.svg)\
-->


Conditional statements don't have to include an `else`.
If there isn't one,
Python simply does nothing if the test is false:

```python
num = 53
print('before conditional...')
if num > 100:
    print('53 is greater than 100')
print('...after conditional')
```

```
before conditional...
...after conditional
```

We can also chain several tests together using `elif`,
which is short for "else if".
The following Python code uses `elif` to print the sign of a number.

```python
num = -3
```

```python
if num > 0:
    print(num, "is positive")
elif num == 0:
    print(num, "is zero")
else:
    print(num, "is negative")
```

```
-3 is negative
```

One important thing to notice in the code above is that we use a double equals sign `==` to test for equality
rather than a single equals sign
because the latter is used to mean assignment.

We can also combine tests using `and` and `or`.
`and` is only true if both parts are true:

```python
if (1 > 0) and (-1 > 0):
    print('both parts are true')
else:
    print('at least one part is false')
```

```python
at least one part is false
```

while `or` is true if at least one part is true:
```python
if (1 < 0) or (-1 < 0):
    print('at least one test is true')
```

```
at least one test is true
```

##While loops
Now we have a little bit of experience using comparison operators to control the flow of our code, we can take a look at another very common form of loop.

The `while` statement allows you to repeatedly execute a block of statements as long as a condition is true. A while statement is an example of what is called a looping statement. A while statement can have an optional else clause.

We begin by looking at one of the simplest dynamic programming algorithms, generating a fibonacci sequence. 


```python
n = int(input("n = "))
f0 = 0
f1 = 1
while n > 1:
    nxt = f0 + f1
    f0 = f1
    f1 = nxt
    n -= 1
print("Fn =", f1)
```

This code inputs an integer n for which it computes and prints the _nth_ Fibonacci number.

>Here is how the algorithm works in a bit more detail:

>* We first initialize (set to their starting values) variables `f0` and `f1` to 0 and 1 respectively.
 
>* Then we run a loop as long as n > 1. In that loop, we

>    * Compute the sum `f0` + `f1` and save it for later in the variable nxt (short of "next", which we don't use because next is a built-in Python function).
    
>    * We assign `f0` = `f1` and `f1` = `nxt`.
>    In other words, the new value of `f0` is equal to the old >value of `f1` and the new value is equal to the sum of old >values of `f0` and `f1`.
    
>    * We reduce `n` by 1.


Note that the `int()` function here converts a string into a an integer. 


And here is the Fibonacci algorithm we developed wrapped in a function:

## From a "regular" code to a function¶

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


The function definition opens with the word `def`, which is followed by the name of the function and a parenthesized list of parameter names. The [body](reference.html#function-body) of the function - the statements that are executed when it runs - is indented below the definition line.

Let's try running our function. Calling our own function is no different from calling any other function:

```python
fibonacci(10)
```
```
10
```

## Challenges

<!--sec data-title="What is truth?" data-id="challenge1" data-show=true ces-->


You just learned about a new type of object in Python. It's called a __Boolean__ -- and it probably is the easiest type there is.

There are only two Boolean objects:`True` and `False`. In python expressions `True` and `False` are special words in which represent true and false statements. 

However, they aren't the only values in Python that are true and false. After reading and running the following `if` statements, explain what the rule is for which values are considered true and which are considered false.

 ```python
 if '':
     print('empty string is true')
 if 'word':
     print('word is true')
 if []:
     print('empty list is true')
 if [1, 2, 3]:
     print('non-empty list is true')
 if 0:
     print('zero is true')
 if 1:
     print('one is true')
 ```


<!--endsec-->

## Resources

> DjangoGirls [Python Basics: Comparisons](https://www.youtube.com/watch?v=7bzxqIKYgf4) video.



<!--sec data-title="Near to me" data-id="challenge2" data-show=true ces-->

Write a function that takes two _floats_ as input parameters, and returns `True` if the value of these floats is within 10 % of one another, e.g. the ratio of the numbers falls in the range `0.9 - 1.1`.

<!--endsec-->
