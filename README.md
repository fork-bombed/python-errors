# Python Errors

Errors can be daunting to new programmers, use this list of errors to discover what's actually going wrong and how you can solve it. I will be building this repository up over time, feel free to contribute, but make sure your submission is in the same template as others.

## Common Errors

* [IndentationError](#IndentationError)
* [TabError](#TabError)
* SyntaxError
* TypeError


## All Errors

* Exception
    * ArithmeticError
        * FloatingPointError
        * OverflowError
        * ZeroDivsionError
    * AssertionError
    * AttributeError
    * BufferError
    * EOFError
    * ImportError
        * ModuleNotFoundError
    * LookupError
        * IndexError
        * KeyError
    * MemoryError
    * NameError
        * UnboundLocalError
    * OSError
        * BlockingIOError
        * ChildProcessError
        * ConnectionError
            * BrokenPipeError
            * ConnectionAbortedError
            * ConnectionRefusedError
            * ConnectionResetError
        * FileExistsError
        * FileNotFoundError
        * InterruptedError
        * IsADirectoryError
        * NotADirectoryError
        * PermissionError
        * TimeoutError
    * ReferenceError
    * RuntimeError
        * NotImplementedError
        * RecursionError
    * StopIteration
    * StopAsyncIteration
    * SyntaxError
        * [IndentationError](#IndentationError)
            * [TabError](#TabError)
    * SystemError
    * TypeError
    * ValueError
        * UnicodeError
            * UnicodeDecodeError
            * UnicodeEncodeError
            * UnicodeTranslateError
    * Warning
        * BytesWarning
        * DeprecationWarning
        * FutureWarning
        * ImportWarning
        * PendingDeprecationWarning
        * ResourceWarning
        * RuntimeWarning
        * SyntaxWarning
        * UnicodeWarning
        * UserWarning
* GeneratorExit
* KeyboardInterrupt
* SystemExit

## IndentationError

Indentation errors are very common in Python since the syntax is dependant on whitespace. 

This can also be caused by mixing your tabs and spaces together. For example, if you were to use a tab to indent a block of code and then use 4 spaces to indent the next, then it will error. This is a common error when copying code online, as it will likely copy as spaces whereas the rest of your code uses tabs or vice versa.

### Problem
This is caused by incorrectly indenting your code. Here is an example of incorrectly indented code:

```python
>>> def add(x,y):
... return x + y
  File "<stdin>", line 2
    return x + y
         ^
IndentationError: expected an indented block
```

### Solution
Make sure that your code has correct indentation. Here is a solution to the above problem:

```python
>>> def add(x,y):
...     return x + y
```

## TabError
TabErrors are usually problems caused by your IDE or text editor converting some tabs into spaces and mixing tabs with spaces.

### Problem
In this example, I've mixed a tab and 4 spaces together and have visualised the tabs as (==) and the spaces as (••):

```python
>>> def get_name():
...  •• name = input('Enter your name: ')
...  == return name
  File "<stdin>", line 3
    return name
              ^
TabError: inconsistent use of tabs and spaces in indentation
```

### Solution
To solve this problem, make sure your IDE or text editor is set to automatically replace tabs with 4 spaces. This will keep your layout consistent:

```python
>>> def get_name():
...     name = input('Enter your name: ')
...     return name
... 
>>> get_name()
Enter your name: John
'John'
```
