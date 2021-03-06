# Python and IPython
---
> A brief detour to terminal, python, and IPython.

Before we start using python in Jupyter environment (`jupyter-lab` or `jupyter-notebook`), let us get some grounding in python and experience a clean and simple python interpreter through terminal. Open your favourite terminal program, preferably one with bash-like shell with `Unix` commands.

---
**Bash-like Shells**

> \[***Unix Commands***\] For a list of commonly used unix commands— special unix programs, please refer to [this link](http://mally.stanford.edu/~sr/computing/basic-unix.html). The most commonly used of these are `man`, `ls`, `cd`, `pwd`, `mkdir`, `cat`, and `less`. If you want to learn or remind yourself on how to use any of these and other unix commands use `man` to lookup manpages of programs (`man command_name`), e.g. try

```
man ls
```

> \[***Mac OS*** \] You can use the default "Terminal" application with `zsh` shell.

> \[***Windows***\] There are many terminals available on windows OS. You can use `cmd.exe` as your command line interface, but as a default I suggest using `windows terminal`. You can install [windows terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab) from the official app store, and install `git bash` (e.g. you can install [git for windows](https://gitforwindows.org), which comes with its own `git bash`). For earlier `Win OS` versions, please try to install the windows terminal, if it is available. As an alternative, you can directly use `git bash` shell. As an added bonus, we will hopefully use `git` in the future, but for now let us just enjoy the bash shell.

---

## Python Interpreter
In terminal, enter following (i.e. type the following characters and press <kbd>enter</kbd> or <kbd>return</kbd> key).
```
python
```

you should see python message similar to the one shown below. Preferably, your python version should be `3.6` and above (e.g. `3.7`, `3.8`, etc.), and if you followed steps in the [getting started section](./0_Getting_started.md) you should also see words `Anaconda, Inc.`.

```python
Python 3.6.9 |Anaconda, Inc.| (default, Jul 30 2019, 13:42:17)
[GCC 4.2.1 Compatible Clang 4.0.1 (tags/RELEASE_401/final)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

The line starting with `>>>` is the prompt where we enter the input to the python interpreter. Let's try adding two integers by entering `1+1` to the prompt, you should see this

```python
>>> 1+1
2
```

## Built-in Types and Variable Assignment

Meet the building blocks of python programming language—[built-in types](https://docs.python.org/3/library/stdtypes.html). Together with [built-in functions](https://docs.python.org/3/library/functions.html) and container datatypes (e.g. see [list](https://docs.python.org/3/library/stdtypes.html#list), [tuple](https://docs.python.org/3/library/stdtypes.html#tuple), [dict](https://docs.python.org/3/library/stdtypes.html#dict)), these will form foundations for all our python code. Let's start with `bool` objects: `True` and `False` (`bool` is built-in data type), and [Boolean operations](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not) such as `or`, `and`, `not`, `==`, `!=`, and `is`.

```python
>>> False
False
>>> True
True
>>> not True
False
>>> True is False
False
>>> True is True
True
>>> True == True
True
>>> True != False
True
```

The `is` operation checks for object identity (i.e. all `True` objects are the same objects, same is true for `False`) and `==` checks for value equality. Similarly, we can construct more complex Boolean expressions (expressions that compute to a `bool` objects `True` and `False`) using all of the above and comparison operations

```python
>>> not 1>2
True
>>> 1>2
False
>>> (not 1==2) is False  # "is" evaluated last
False
>>> not 1==2 is False  # "not" evaluated last
True
```

note that there is an order of precedence for the operations ([you can read more about priority of Boolean operations here](https://docs.python.org/3/library/stdtypes.html#boolean-operations-and-or-not)). Python is case-sensitive, so this will result is error

```python
>>> true
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'true' is not defined
```

also note that we have used `==` to check for equality, as `=` is used for variable assignment. For instance, lets assign value (`int`) to variable named `x`

```python
>>> x = 1
>>> x
1
```

---
> You can use any name for your variables. ***This means that you need to be careful to not overwrite built-in objects in python***. For example, do not do this

```python
>>> print=5  # now print() is overwritten`
>>> print
5
```

> Python allows assigning multiple variables on one go, e.g. `x, y, z = 1, 'abc', 3/4`.

---

Now object `x`, our variable, has value `1` (`int` data type) and we can use `x` anywhere you would use `int` 1.

```python
>>> x+x
2
>>> x == 1
True
>>> x == 1.0
True
>>> x == 2
False
>>> x > 0
True
```

Built-in functions also include basic mathematical operations, here are some of them:

```python
>>> x/2  # division
0.5
>>> x//2  # integer division
0
>>> round(1.2)  # rounding return integer
1
>>> abs(-123.2)  # absolute value
123.2
>>> 2*2  # multiplying two integers
4
>>> 2.*2  # multiplying float and integer
4.0
>>> 2**2  # taking power of integer, ie. 2^2
4
>>> pow(2,2)  # same as 2**2
4
>>> 5%2  # remainder or modulus operation
1
>>> 2*(5//2)+5%2
5
```

## Importing Modules
Standard mathematical operations we used above could be limiting for certain applications. For this reason, python comes with [`math`](https://docs.python.org/3/library/math.html) module, which includes functions such as `exp()`, `log()`, trigonometric functions and more. While we are at it let us also learn importing external python modules with [`import`](https://docs.python.org/3/glossary.html#term-import-path) keyword.


```python
>>> import math  # imports math module
>>> math
<module 'math' from '/Users/USER/anaconda3/lib/python3.6/lib-dynload/math.cpython-36m-darwin.so'>
>>> math.exp(2)
7.38905609893065
>>> math.exp(10)
22026.465794806718
>>> math.log(math.exp(2))
2.0
>>> math.log10(10**(2))
2.0
```

We can also use aliases for modules when importing.
```python
>>> import numpy as np  # numerical python library
>>> import matplotlib.pyplot as plt  # `pyplot` module in plotting library `matplotlib`
>>> np.e  # Euler's number
2.718281828459045
>>> np.pi  # pi
3.141592653589793
>>> math.e
2.718281828459045
>>> math.pi
3.141592653589793
```
This allows us to use short and convenient names such as `np` and `plt` instead of longer `numpy` and `matplotlib.pyplot` in our code.

## Some Useful Python Functions
### `type()`
You can check type of all variables (i.e. objects) in python using `type()` function, this will be very useful for debugging your own code and understanding code written by others.

```python
>>> type(True)
<class 'bool'>
>>> type(1)
<class 'int'>
>>> type(1.)
<class 'float'>
>>> float(1)  # typecast/convert integer to float
1.0
>>> 1.  # adding decimal "." tells python to treat input as float
1.0
>>> 2039349
2039349
>>> type(203484)
<class 'int'>
```

### `print()`, `repr()` and `str`
`print()` function prints to standard output `sys.stdout`, e.g. prompts shown above, or a file object. Outputs from the expressions that we have been entering above, that are evaluated to some values, and prompts of built-in function `input()` are sent to `sys.stdout`. `print()` accepts any object and all non-keyword arguments to it are converted to strings (`str` type).

```python
>>> print(x)
1
>>> print("abc")
abc
>>> print('abc', 2 ,10.0)
abc 2 10.0
>>> print('abc', 2 ,10.0, end='')
abc 2 10.0>>>
>>> print('abc', 2 ,10.0, end='\n\n')
abc 2 10.0


>>> print('abc\n\tdef')
abc
	def
```

where `\n`, and `\t` are the new line and tab characters respectively, and note how we set the last character to print with `end=` keyword argument (`end=''` prints an empty string, default is `end='\n'`). If we want to ignore special characters like `\t` and `\n` and print them literally, we can use `raw` string

```python
>>> r'abc\ndef'  # raw string; note how it adds a skip character `\`
'abc\\ndef'
>>> print(r'abc\ndef')
abc\ndef
```

As you have probably guessed, you can construct strings (`str` objects) using `"` quotes and single quotes `'`, and raw strings by adding `r` in front (e.g. `r"abc"`). Similarly, you can convert any object to its string representation using `str()` (see also `repr()`, spot any differences?)

```python
>>> 'abc123'
'abc123'
>>> "abc123"
'abc123'
>>> r"abc123"  # this will make no difference; no special characters here
'abc123'
>>> str
<class 'str'>
>>> str(1)  # int to str
'1'
>>> str(123)  # int to str
'123'
>>> str(1.)  # float to str
'1.0'
```

###  `dir()` and `help()`
When working with new and unfamiliar objects and variables you might find function `dir()`  very useful. `dir()` lists all object's attributes which allows you to "browse" through what is inside the object. For instance, let's list all attributes of `x` (which is `int` type).

```python
>>> x = 1  # assign integer to x
>>> print(x)
1
>>> dir(x)
['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 'numerator', 'real', 'to_bytes']
```
You can access all these attributes. Let's use `__float__` and `__eq__` methods of `x`.

```python
>>> x.__float__()
1.0
>>> x.__eq__(3)  # same as `x == 3`
False
```
In fact, these methods are used when we are operating on our object `x` (e.g. `x == 3` uses `x.__eq__()`). We can also list attributes of classes as well as objects (you can also use `dir()` with functions, as in Python functions are objects as well), e.g. here for `str` class.

```python
>>> dir(str)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
>>> my_string = 'Abcd'
>>> my_string
'Abcd'
>>> my_string.capitalize()
'Abcd'
>>> my_string.upper()
'ABCD'
```

Another very useful function for understanding objects is `help()`. `help()` will open the documentation if it is available (special comments section of the class, or function)

```python
>>> help(math.ceil)  # press Q to close help
>>> help(x)
>>> help(str)
```

> ***Tip*** : For long documentation `help()` opens a separate "window", which you can close by pressing <kbd>Q</kbd> after you finish reading it.

> As a practice exercise, use `dir` and `help` to learn about `str.format()`, other objects, and their methods and attributes.
E.g. create a string and use `dir` to explore it, then open help for `str.format()` for your string
(e.g. `"".format()`, here the first part `""` returns a new string).

## For and While Loops

```python
>>> for k in 'abcd':
...     print(k)  # indented line; preferably use spaces
...
a
b
c
d
>>> for k in range(3):
...     print(k)
...
0
1
2
>>> k = 0
>>> while k<4:  # "k<4" part should evaluate to `bool` True/False
...     # do something here
...     k+=1  # this will make sure that we don't get an infinite loop
...     print(k)
...
1
2
3
4
```

> ***Tip*** : if you accidentally run an infinite `while` loop or a long and computationally intensive
`for` loop and want to cancel your command, use <kbd>Ctrl</kbd> + <kbd>C</kbd> to cancel and exit the loop.

```python
>>> s = 'abcd'
>>> for k in range(len(s)):
...     print(k,':', s[k])
...
0 : a
1 : b
2 : c
3 : d
```

nested for loops
```python
>>> for k in range(3):
...     # outer for loop
...     for m in range(2):
...             # inner for loop
...             print([k,m]) # check your indentations in code blocks
...
[0, 0]
[0, 1]
[1, 0]
[1, 1]
[2, 0]
[2, 1]
```

### Conditional Statements
```python
>>> s = 'Hello, world!'
>>> if len(s)>20:
...     print('1')
... elif len(s)>15:
...     print('2')
... else:
...     print('3')
...
3
```

> Python also provides functions for parallel iteration over several sequences, and enumerating
sequences. *See [`zip`](https://docs.python.org/3/library/functions.html#zip) and [`enumerate`](https://docs.python.org/3/library/functions.html#enumerate)*.    

---
> ***Exercise*** : For all integers `n` in range \[0, 50\], depending on whether `n` is
an even or an odd number, on a new line print integer `n` itself (i.e. once) if it
is even, or if it is an odd number print `n` `n` number of times on a single line.
E.g. for 2 print line `2` and for 3 print line `3 3 3`. Do this once with nested for loops,
and once with a single for loop. (*Hints*: you may find modulus function `%` useful; 3*"ab"
returns "ababab").

After you are done practicing, you can close python interpreter by entering
```python
>>> exit()
```

---

## IPython- Interactive Python Shell and Kernel for Jupyter
In terminal, enter

```
ipython
```

This starts IPython shell, where you should see a message similar to the one shown below.

```python
Python 3.6.9 |Anaconda, Inc.| (default, Jul 30 2019, 13:42:17)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.8.0 -- An enhanced Interactive Python. Type '?' for help.
```

IPython adds a lot of additional features to the standard python interpreter. First, note the line numbers for inputs and outputs. Isn't it pretty?!

```python
In [1]: import math

In [2]: math
Out[2]: <module 'math' from '/Users/USER/anaconda3/lib/python3.6/lib-dynload/math.cpython-36m-darwin.so'>

In [3]: x = 1

In [4]: x
Out[4]: 1

In [5]: print(x)
1

```

Next, we can send commands to your system (shell) by prefixing `!` character to the shell commands.

```python
In [6]: !which python
/Users/USER/anaconda3/bin/python
```

In additon to that we get IPython magic commands. Please read more about [magic commands here](https://ipython.readthedocs.io/en/stable/interactive/magics.html#).

```python
In [7]: %ls
AnacondaProjects/                            Pictures/
Applications/                                Public/
Desktop/                                     anaconda3/
Documents/        
Downloads/      
Dropbox/                            
Library/    
Movies/   
Music/    
In [8]: %whos
Variable   Type      Data/Info
------------------------------
math       module    <module 'math' from '/Use<...>h.cpython-36m-darwin.so'>
x          int       1

In [9]: import numpy as np  # import another module

In [10]: %whos
Variable   Type      Data/Info
------------------------------
math       module    <module 'math' from '/Use<...>h.cpython-36m-darwin.so'>
np         module    <module 'numpy' from '/Us<...>kages/numpy/__init__.py'>
x          int       1
```

See how `whos` lists all variables (objects) in your IPython environment with their names (`Variable`) and values (`Data/Info`)? Do you remember typing a very long `help()` function to lookup documentation for functions and objects, well in IPython you just add suffix `?` to your function/object to do the same.

```python
In [11]: list?
Init signature: list(self, /, *args, **kwargs)
Docstring:
list() -> new empty list
list(iterable) -> new list initialized from iterable's items
Type:           type
Subclasses:     _HashedSeq, StackSummary, SList, List, List, List, List, _ImmutableLineList, FormattedText, NodeList, ...

In [12]: np.ones?
```
But joking aside, this will come in handy when you are writing your own code in IPython and Jupyter and want to quickly lookup help for functions.

>Reminder : use <kbd>Q</kbd> to close the help window.

Let's get back to learning python, now using IPython.

## Lists, Tuples, Dictionaries

As mentioned above, python has built-in container datatypes
[list](https://docs.python.org/3/library/stdtypes.html#list),
[tuple](https://docs.python.org/3/library/stdtypes.html#tuple), and
[dict](https://docs.python.org/3/library/stdtypes.html#dict).

> In addition to these, module [collections](https://docs.python.org/3/library/collections.html#module-collections)
provides more specialised container datatypes that complement and extend these three built-in containers.

### Lists

We can construct lists using the square brackets `[]`, or by converting iterable object,
i.e. any python object that allows iterating over it, e.g. `str`, using `list()` function
(this calls the initialisation function of a list object `__init__()` and constructs a new
list object from the input `iterable` object). You can access list elements by indexing
them (indexing starts from `0`), e.g. `a[0]` and `a[-1]` return first and last elements of
a list `a`
```python
In [13]: [1,2,3]
Out[13]: [1, 2, 3]

In [14]: l = [1,2,3]  

In [15]: l[0]
Out[15]: 1

In [16]: l[1]
Out[16]: 2

In [17]: l[3]
---------------------------------------------------------------------------
IndexError                                Traceback (most recent call last)
<ipython-input-17-bb49eeb9f0db> in <module>
----> 1 l[3]

IndexError: list index out of range

In [18]: l[2]
Out[18]: 3

In [19]: l[-1]  # last element
Out[19]: 3

In [20]: len(l)
Out[20]: 3

In [21]: list('abcde')
Out[21]: ['a', 'b', 'c', 'd', 'e']                                                      

In [22]: range(10)  # returns `range` iterator object
Out[22]: range(0, 10)

In [23]: l = list(range(10))

In [24]: l
Out[24]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [25]: l[0]
Out[25]: 0

In [26]: l[1] + 1
Out[26]: 2

In [27]: l
Out[27]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
Note that we get an error message when we try to access fourth element `l[3]`
(that does not exist) in a list with only three elements.

> ***Tip 1***: use `len()` to check number of elements in container objects.

> ***Tip 2***: you can create number sequences using `range()` and `list()`/`tuple()`.

---
> ***Warning***: Using variable names `l`, `I`, and `O` can be confusing, e.g. `l` can be misread as `I`, and
is a practice that is frowned upon.

> ***Unpacking lists*** : Lists can be used to assign multiple variables in one go by unpacking them.

```python
>>> L = [1, 2, 'ab']
>>> x, y, z = L  # needs same number of variable names
>>> L1, *Lrest = L  # unpacks 1st element to L1 and the rest of the list to Lrest
>>> print("x={}; y={}; z={}; L1={}; Lrest={}".format(x, y, z, L1, Lrest))
x=1; y=2; z=ab; L1=1; Lrest=[2, 'ab']
```

---

### Changing List Elements, and Slicing
You can access and change one element in a list by assigning new value to an element in the list, or a set of elements by slicing the list
```python
In [27]: l[3] = -10  # assign new value to 4th element

In [28]: l[-3:]   # slice the list   
Out[28]: [7, 8, 9]

In [29]: l[-3:] = [0,0,0] # assigning an iterable with the same length as the slice

In [30]: l
Out[30]: [0, 1, 2, -10, 4, 5, 6, 0, 0, 0]
```


### Appending to and Extending Lists, `pop()`, `del`, and `copy()`
```python
In [31]: l.append('abc')

In [32]: l.append(math.e)

In [33]: l
Out[33]: [0, 1, 2, -10, 4, 5, 6, 0, 0, 0, 'abc', 2.718281828459045]

In [34]: len(l)
Out[34]: 12

In [35]: l.pop()  # pop the last element
Out[35]: 2.718281828459045

In [36]: l.pop()  # pop the last element
Out[36]: 'abc'

In [37]: len(l)
Out[37]: 10

In [38]: l
Out[38]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [39]: l.extend(['abc'])  # extend `l` with `['abc']`

In [40]: l.extend('abc')  # input can be any iterable, e.g. `str` object

In [41]: l
Out[41]: [0, 1, 2, -10, 4, 5, 6, 0, 0, 0, 'abc', 'a', 'b', 'c']

In [42]: l.extend(range(2))

In [43]: l
Out[43]: [0, 1, 2, -10, 4, 5, 6, 0, 0, 0, 'abc', 'a', 'b', 'c', 0, 1]
```

Let's use `del` function to delete all elements starting with index `5` to the last element in `l`.
```python
In [44]: del l[5:]  # delete all elem-s starting with and including index `5`

In [45]: l
Out[45]: [0, 1, 2, -10, 4]
```

---
>You can use `del` to delete all elements in the list, e.g. `del l[:]`, or delete the variable `l` (whole list)

```python
del l  # deletes variable `l`
```

---

Assigning lists to a new variable name does not create a new list, and changing one will change the other. To avoid assigning the same object to the new name, use `copy()` (see also [deepcopy](https://docs.python.org/3/library/copy.html)).
```python
In [46]: a = l  # now var "a" points to var "l"

In [47]: a is l  # a and l are the same object
Out[47]: True

In [48]: b = l.copy()  # copy list elements to a new list

In [49]: b is l  # b and l are different objects
Out[49]: False

In [50]: b == l  # b and l elements are equal to each other
Out[50]: True

In [51]: a[0]=100  # modifying "l" modifies "a"

In [52]: a
Out[52]: [100, 1, 2, -10, 4]

In [53]: l                                                                      
Out[53]: [100, 1, 2, -10, 4]

In [54]: b
Out[54]: [0, 1, 2, -10, 4]

In [55]: l.sort()  # changes l and a

In [56]: l                                                                      
Out[56]: [-10, 1, 2, 4, 100]

In [57]: a                                                                      
Out[57]: [-10, 1, 2, 4, 100]
```
### Tuples
[Tuples](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences) are another standard
sequences data type in python similar to strings and lists. Compared with lists, tuples
and strings are [immutable](https://docs.python.org/3/glossary.html#term-immutable), but same as lists their elements
can be accessed by indexing and slicing. You can create tuples using brackets `()`, or by assigning a number of values
separated by commas to a single variable.

```python
In [58]: t = ()  # an empty tuple

In [59]: t2 = ('abc', )  # tuple with one element

In [60]: t3 = 1, 2 , t2  # tuple packing; heterogenous sequence

In [61]: print(f't: {t}/nt2: {t2}/nt3: {t3}')  # print variables
t: ()
t2: ('abc',)
t3: (1, 2, ('abc',))

In [62]: t3[-2]
Out[62]: 2

In [63]: t[0] = 0   # tuples are immutable and can't be changed
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-63-51595a4035f3> in <module>
----> 1 t[0] = 0

TypeError: 'tuple' object does not support item assignment
```

---

> ***Tuple Unpacking***: Tuple unpacking is a common way to assign values to multiple variables, e.g.

```python
>>> x, y, z = 1 , 2, 'abc'  # equivalent to ` x, y, z = (1 , 2, 'abc') `
```

---

### Dictionaries
Dictionary (`dict`) is another mutable container data type in python that represent a set of (key, value) pairs.
Compared to lists, strings, and tuples which use numbers as indices, `dict` uses keys as indices. Keys can be of any
immutable data type (e.g. `int`, `str`, `tuple`, etc.). Following are examples for creating dictionaries.

```python
In [64]: d = {'a': 2, 1: 'b', 'c': 10}

In [65]: d
Out[65]: {'a': 2, 1: 'b', 'c': 10}

In [66]: dict(((1,2), ('a', 3), 'ed', ['hello', 10]))
Out[66]: {1: 2, 'a': 3, 'e': 'd', 'hello': 10}
```

You can use use the `in` keyword to check whether a key is in the dictionary. Like other containers we saw above,
`dict` type objects are iterable, but compared to for instance `list`, in dictionaries we iterate over the keys. Applying `list()`
on a dictionary returns a list of keys, and applying `sorted()` returns sorted list of keys.

```python
In [67]: 'c' in d
Out[67]: True

In [68]: 1 in d
Out[68]: True

In [69]: 10 in d
Out[69]: False

In [70]: for k in d:
    ...:     print('key: ',k,'; value: ', d[k])
    ...:     
key:  a ; value:  2
key:  1 ; value:  b
key:  c ; value:  10

In [71]: list(d)
Out[71]: ['a', 1, 'c']

In [72]: d2 = {'c':0, 'a':1, 'b':2}

In [73]: d2
Out[73]: {'c': 0, 'a': 1, 'b': 2}

In [74]: sorted({'c':0, 'a':1, 'b':2})
Out[74]: ['a', 'b', 'c']
```

### List Comprehensions, and Dict comprehensions
> More about: [list compehensions](https://docs.python.org/3/tutorial/datastructures.html#list-comprehensions).

Another convenient way to create lists in python is to use list comprehensions. E.g.:

```python
In [75]:  l = [k for k in range(10)]

In [76]: l            
Out[76]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [77]: [k for k in 'abcde']
Out[77]: ['a', 'b', 'c', 'd', 'e']

In [78]: [(k,m) for k in range(2) for m in range(3)]  # list of tuples
Out[78]: [(0, 0), (0, 1), (0, 2), (1, 0), (1, 1), (1, 2)]
```
Similarly for dictionaries we can use "dict comprehensions", as long as keys are
immutable types.

```python
In [79]: {k: k+k for k in range(3)}
Out[79]: {0: 0, 1: 2, 2: 4}

In [80]: {k : v for k, v in zip(['a', 'b' , 'see'], range(3))}
Out[80]: {'a': 0, 'b': 1, 'see': 2}
```

## Numpy and Its Friends
It's all good, but using built-in lists/tuples/dict/ etc. is not convenient when
working with arrays, and how do you even do plotting?! For instance, in Matlab
there are purpose built data types and operations for working with arrays
(e.g. arrays, and linear algebra tools). Python's built-in modules do not include
such tools, instead Python users generally use various specialised packages such
as [`numpy`](https://numpy.org) for array operations,
[`scipy` library](https://www.scipy.org) for linear algebra, statistics,
numerical integration and other numerical functions, and
[`matplotlib`](https://matplotlib.org) for plotting and visualisation. Your standard
Anaconda installation comes with all these packages and more.

Numpy and Matplotlib provides functions, or interfaces for their functions, with Matlab-like syntax.
Following code snippets should be familiar to Matlab users.

```python
In [81]: import numpy as np                                                     

In [82]: np.ones?                                                               

In [83]: np.ones(10)                                                            
Out[83]: array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])

In [84]: np.ones((2,10))                                                        
Out[84]:
array([[1., 1., 1., 1., 1., 1., 1., 1., 1., 1.],
       [1., 1., 1., 1., 1., 1., 1., 1., 1., 1.]])
```

> Depending on your system and IPython version, you might need to set a backend for Matplotlib's using
`%matplotlib` (this uses the default backend, starting with `IPython 5.0` and `matplotlib 2.0` this
step is not required).

```python       
In [85]: import matplotlib.pyplot as plt  # pyplot interface to matplotlib                                  

In [86]: import matplotlib

In [87]:  %matplotlib   #  ipython magic to set matplotlib backend
Using matplotlib backend: Qt5Agg

In [88]: x, y = np.linspace(-10,10,100), np.random.rand(100)

In [89]: plt.plot(x, y, '-o', mfc='r', ms=10, label='Uniform noise')  # this returns Line2D object
Out[89]: [<matplotlib.lines.Line2D at 0x7fa98d1fb940>]

In [90]: plt.plot(x, 0.5*np.ones(100), 'b', alpha=0.5, lw=3);  # ; suppresses output from plot

In [91]: plt.xlabel('x');

In [92]: plt.ylabel('y');                                                      

In [93]: plt.title('Title'); plt.legend();

In [94]: plt.show()
```
![](./images/example_plot.png)
---

Please follow these links to learn more about NumPy and other packages that we will use soon:
- \[      ***Arrays***    \] [numpy tutorial](https://numpy.org/doc/stable/user/quickstart.html)
to get an overview of `numpy`, and [https://numpy.org/learn/](https://numpy.org/learn/) for
more NumPy tutorials.
- \[    ***Plotting***   \] [matplotlib tutorials](https://matplotlib.org/stable/tutorials/index.html#advanced), esp. [`matplotlib.pyplot` tutorial](https://matplotlib.org/stable/tutorials/introductory/pyplot.html#sphx-glr-tutorials-introductory-pyplot-py).
- \[***Linear Algebra, Numerical comp-s***\] [scipy guide](https://www.scipy.org/getting-started.html)
- \[***Image Analysis***\] [scikit-image guide](https://scikit-image.org/docs/dev/user_guide/getting_started.html)
- \[ ***Data Analysis*** \] [pandas introduction](https://pandas.pydata.org/docs/getting_started/index.html#intro-to-pandas)

---

## Closing Python Interpreter and IPython Shell
Use `exit()` or <kbd>Ctrl</kbd> + <kbd>D</kbd>.
```python
exit()
```
