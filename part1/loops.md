# Loops

> ## Learning Objectives
>
> *   Explain what a for loop does.
> *   Correctly write for loops to repeat simple calculations.
> *   Trace changes to a loop variable as the loop runs.
> *   Trace changes to other variables as they are updated by a for loop.

An example task that we might want to repeat is printing each character in a
word on a line of its own. One way to do this would be to use a series of `print` statements:

```python
word = 'lead'
print(word[0])
print(word[1])
print(word[2])
print(word[3])
```

```
l
e
a
d
```

This is a bad approach for two reasons:

1.  It doesn't scale:
    if we want to print the characters in a string that's hundreds of letters long,
    we'd be better off just typing them in.

1.  It's fragile:
    if we give it a longer string,
    it only prints part of the data,
    and if we give it a shorter one,
    it produces an error because we're asking for characters that don't exist.

```
word = 'tin'
print(word[0])
print(word[1])
print(word[2])
print(word[3])
```
```
t
i
n
```
```
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-3-7974b6cdaf14> in <module>()
      3 print(word[1])
      4 print(word[2])
----> 5 print(word[3])

IndexError: string index out of range
```


Here's a better approach:

```
word = 'lead'
for char in word:
    print(char)
```

```
l
e
a
d
```

This is shorter---certainly shorter than something that prints every character in a hundred-letter string---and
more robust as well:

```python
word = 'oxygen'
for char in word:
    print(char)
```

```
o
x
y
g
e
n
```

The improved version uses a [for loop](reference.html#for-loop)
to repeat an operation---in this case, printing---once for each thing in a collection.
The general form of a loop is:

```python
for variable in collection:
    do things with variable
```

We can call the [loop variable](reference.html#loop-variable) anything we like,
but there must be a colon at the end of the line starting the loop,
and we must indent anything we want to run inside the loop. Unlike many other languages, there is no
command to signify the end of the loop body (e.g. end for); what is indented after the for statement belongs to the loop.

Here's another loop that repeatedly updates a variable:

```python
length = 0
for vowel in 'aeiou':
    length = length + 1
print('There are', length, 'vowels')
````

```python
There are 5 vowels
```

It's worth tracing the execution of this little program step by step.
Since there are five characters in `'aeiou'`,
the statement on line 3 will be executed five times.
The first time around,
`length` is zero (the value assigned to it on line 1)
and `vowel` is `'a'`.
The statement adds 1 to the old value of `length`,
producing 1,
and updates `length` to refer to that new value.
The next time around,
`vowel` is `'e'` and `length` is 1,
so `length` is updated to be 2.
After three more updates,
`length` is 5;
since there is nothing left in `'aeiou'` for Python to process,
the loop finishes
and the `print` statement on line 4 tells us our final answer.

Note that a loop variable is just a variable that's being used to record progress in a loop.
It still exists after the loop is over,
and we can re-use variables previously defined as loop variables as well:

```python
letter = 'z'
for letter in 'abc':
    print(letter)
print('after the loop, letter is', letter)
```

```
a
b
c
after the loop, letter is c
```

Note also that finding the length of a string is such a common operation
that Python actually has a built-in function to do it called `len`:

```python
print(len('aeiou'))
```

```
5
```

`len` is much faster than any function we could write ourselves,
and much easier to read than a two-line loop;
it will also give us the length of many other things that we haven't met yet,
so we should always use it when we can.

If we loop over a list, which we learnt about in the previous lesson, the loop variable is assigned elements one at a time:

```python
odds = [1, 3, 5, 7]
for number in odds:
    print(number)
```
```
1
3
5
7
```

## Range

Python has a built-in function called `range` that creates an _iterator_ for sequence of numbers. In a nutshell, it generates special type of a Python object, which is generally used to iterate over with for loops. 


In basic terms, if you want to use range() in a for loop, then you're good to go. However you can't use it purely as a list object.

```python
for thingo in range(4):
    print(thingo)
```

```
0
1
2
3
```

<!--sec data-title="Computing powers with loops" data-id="challenge" data-show=true ces-->

Exponentiation is built into Python:

```python
print(5 ** 3)
```

```
125
```

Write a loop that calculates the same result as `5 ** 3` using multiplication (and without exponentiation).

<!--endsec-->

<!--sec data-title="Reverse a string" data-id="challenge" data-show=true ces-->

Write a loop that takes a string, and produces a new string with the characters in reverse order, so `'Newton'` becomes `'notweN'`.

<!--endsec-->
