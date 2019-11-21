# Python Errors

Errors can be daunting to new programmers, use this list of errors to discover what's actually going wrong and how you can solve it. I will be building this repository up over time, feel free to contribute, but make sure your submission is in the same template as others.

### Common Errors

* [ImportError](#ImportError)
* [IndexError](#IndexError)
* [KeyError](#KeyError)
* [NameError](#NameError)
* [SyntaxError](#SyntaxError)
* [IndentationError](#IndentationError)
* [TabError](#TabError)
* [TypeError](#TypeError)
* [ValueError](#ValueError)


### All Errors

* ArithmeticError
    * FloatingPointError
    * OverflowError
    * ZeroDivsionError
* AssertionError
* AttributeError
* BufferError
* EOFError
* [ImportError](#ImportError)
    * [ModuleNotFoundError](#ImportError)
* LookupError
    * [IndexError](#IndexError)
    * [KeyError](#KeyError)
* MemoryError
* [NameError](#NameError)
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
* [SyntaxError](#SyntaxError)
    * [IndentationError](#IndentationError)
        * [TabError](#TabError)
* SystemError
* [TypeError](#TypeError)
* [ValueError](#ValueError)
    * UnicodeError
        * UnicodeDecodeError
        * UnicodeEncodeError
        * UnicodeTranslateError
### Warnings
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

### Exceptions
* BaseException
    * Exception
    * GeneratorExit
    * KeyboardInterrupt
    * SystemExit

## ImportError
This is caused when a module can't be imported correctly. This is most likely caused by mispelling the module name or not having the module installed. <br/>In versions **3.6+** this will throw `ModuleNotFoundError`

### Problem
If you try to import a module that doesn't exist, it will throw an error:
```python
>>> import fakemodule
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'fakemodule'
```

### Solution
Make sure that you spelled your module name correctly and that you have it installed. To install your module, you can use **pip**:
##### Python 2.x
`pip install fakemodule`
##### Python 3.x
`python3 -m pip install fakemodule`<br/>
or
<br/>`pip3 install fakemodule`

## IndexError
This is caused when you try to access an index in a list that doesn't exist.

### Problem
If you're trying to check if an index exists, a common mistake is to check if the index isn't null, but this will just error if the index doesn't exist:
```python
>>> x = ['a','b','c','d']
>>> if x[4] != None:
...     print(x[4])
... 
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

### Solution
Instead of checking the index, you should check the length of the list to make sure that you're not trying to access an index that doesn't exist:
```python
>>> x = ['a','b','c','d']
>>> if len(x) == 5:
...     print(x[4])
... 
     # Prints nothing because the array has a lenght of 4
     # Add another letter to the array to test it
>>> x = ['a','b','c','d','e']
>>> if len(x) == 5:
...     print(x[4])
... 
e
```

## KeyError
This is caused when you try to access a key that doesn't exist in a dictionary.

### Problem
In this scenario, I have a list of country populations. If the country I want the population of doesn't exist, it will error:
```python
>>> population = {'USA':'327.2 million','China':'1.386 billion','UK':'66.44 million'}
>>> population['France']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'France'
```

### Solution
There is a simple solution to this: `dict.get(key[, value])`<br/>
We can use this to check if the key exists and, if not, return a default value:
```python
>>> population = {'USA':'327.2 million','China':'1.386 billion','UK':'66.44 million'}
>>> population.get('France','Unknown')
'Unknown'
>>> population.get('USA','Unknown')
'327.2 million'
```

## NameError
Name errors are usually caused by typos in your variable names or by trying to access a variable that is not in scope.

### Problem
In this example, I try to access a variable that has been defined in a local scope (inside the `get_name()` function):
```python
>>> def get_name():
...     name = input('Enter your name: ')
...     print('Your name is ' + name)
... 
>>> get_name()
Enter your name: John
Your name is John
>>> print(name)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'name' is not defined
```

### Solution
To get variables from within a function, you can return the variable at the end of your function:
```python
>>> def get_name():
...     name = input('Enter your name: ')
...     return name
... 
>>> name = get_name()
Enter your name: John
>>> name
'John'
```
You can also set a global variable outside the scope of the function and access it by using the `global` keyword:
```python
>>> name = 'John'
>>> def get_name():
...     global name
...     name = input('Enter your name: ')
... 
>>> name
'John'
>>> get_name()
Enter your name: Jane
>>> name
'Jane'
```

## SyntaxError
Syntax errors are usually caused by typos in your program.

### Problem
If you spelled a keywork incorrectly it can cause your program to crash:

```python
>>> def add(x,y):
...     retrun x + y
  File "<stdin>", line 2
    retrun x + y
           ^
SyntaxError: invalid syntax
```

### Solution
Make sure that all your keywords are spelled correctly. Here is the solution:
```python
>>> def add(x,y):
...     return x + y
... 
>>> add(1,2)
3 
```

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
Tab errors are usually problems caused by your IDE or text editor converting some tabs into spaces and mixing tabs with spaces.

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

## TypeError
Type errors are caused by applying an operation or function on incompatible types. 

### Problem
The most common occurence of this is concatenating strings and integers. In the example below, I try to add the age to the string I'm about to print:
```python
>>> def print_age(x):
...     print('Your age is: ' + x)
... 
>>> print_age(25)
Traceback (most recent call last):    
  File "<stdin>", line 1, in <module> 
  File "<stdin>", line 2, in print_age
TypeError: must be str, not int  
```

### Solution
In order to add the integer to the string, you'll need to conver the integer into a string by using `str()`. Here is the solution to the above problem:
```python
>>> def print_age(x):
...     print('Your age is: ' + str(x))
... 
>>> print_age(25)
Your age is: 25
```

## ValueError
Value errors are caused when a function or operation received an argument that has the right type but the value isn't correct.

### Problem
This is a common issue when converting strings to integers. If the string does not contain a number, then it cannot be converted:
```python
>>> def convert(number):
...     return int(number)
... 
>>> convert('two')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in convert
ValueError: invalid literal for int() with base 10: 'two'
```

### Solution
This can be solved by checking if the string can be converted by using `str.isnumeric()`:
```python
>>> def convert(number):
...     if number.isnumeric():
...             return int(number)
... 
>>> convert('two')
>>> convert('2')
2
```