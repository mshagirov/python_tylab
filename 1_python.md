# Python and IPython
---
> A brief detour to terminal, python, and IPython.

Before we start using python in the jupyter environment (`jupyter-lab` or `jupyter-notebook`), let us get some grounding in python and experience a clean and simple python interpreter through terminal. Open your favourite terminal program with bash-like shell with `Unix` commands.

---
\[**Mac OS**\] You can use the default "Terminal" application with `zsh` shell.

\[**Windows**\] There are many terminals available on windows OS. You can use `cmd.exe` as your command line interface, but as a default I suggest using `windows terminal`. You can install [windows terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab) from the official app store, and install `git bash` (e.g. you can install [git for windows](https://gitforwindows.org), which comes with its own `git bash`). For earlier `Win OS` versions, please try to install the windows terminal, if it is available. As an alternative, you can directly use `git bash` shell. As an added bonus, we will hopefully use `git` in the future, but for now let us just enjoy the bash shell.

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
You can use any name for your variables. This means that you need to be careful to not overwrite built-in objects in python. For example, do not do this
```python
>>> print=5  # now print() is overwritten`
>>> print
5
```
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
Standard mathematical operations we used above could be limiting for certain applications. For this reason, python comes with [`math`](https://docs.python.org/3/library/math.html) module, which includes functions such as `exp()`, `log()`, trigonometric functions and more. While we are at it let us also learn importing external python modules with keyword: `import`.


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
>>> 1.  # adding decimal "." tell python to treat input as float
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
When working with new and unfamiliar objects and variables you might find function `dir()` which lists all obejct's attributes ("browse" through what is inside the object) very useful. For instance, let's list all attributes of `x` (which is `int` type).

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
In fact, these methods are used when we are operating on our object `x` (e.g. `x == 3` uses `x.__eq__()`). We can also list attributes of classes as well as objects (in python functions are objects as well), e.g. here for `str` class.

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
>>> help(x)
>>> help(math.ceil)
>>> help(str)
```
For long documentation `help()` opens a window which you can close by pressing <kbd>Q</kbd> after you finish reading it.

## IPython- Interactive Python Shell and Kernel for Jupyter
In terminal, enter

```
ipython
```

This starts IPython shell, where you should see following message.

```python
Python 3.6.9 |Anaconda, Inc.| (default, Jul 30 2019, 13:42:17)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.8.0 -- An enhanced Interactive Python. Type '?' for help.
```

IPython adds a lot additional features to the python interpreter that we used above. First, note the line numbers for inputs and outputs. Isn't it pretty?!

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

See how `whos` lists all variables (objects) in your IPython environment with their names (`Variable`) and values (`Data/Info`)? Do remember typing a very long `help()` function to lookup documentation for functions and objects, well in IPython you just add suffix `?` to your function/object to do the same.

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

> Use <kbd>Q</kbd> to close the help window.

Let's get back to learning python, now using IPython.

## Lists, Tuples, Dictionaries

As mentioned above, python has built-in container datatypes [list](https://docs.python.org/3/library/stdtypes.html#list), [tuple](https://docs.python.org/3/library/stdtypes.html#tuple), and [dict](https://docs.python.org/3/library/stdtypes.html#dict).

> In addition to these, module [collections](https://docs.python.org/3/library/collections.html#module-collections) provides more specialised container datatypes that complement and extend these three built-in containers.

We can construct lists using the square brackets `[]`, or by converting iterable object, i.e. any python object that allows iterating over it, e.g. `str`, using `list()` function (this calls the initialisation function of a list object `__init__()` and constructs a new list object from the input `iterable` object). You can access list elements by indexing them (indexing start from `0`), e.g. `a[0]` and `a[-1]` return first and last elements of a list `a`
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
```
Note how when get an error message when we try to access fourth element `l[3]` of a list with only three elements.

> Tip 1: use `len()` to check number of elements in container objects.

> Tip 2: you can create number sequences using `range()` and `list()`/`tuple()`.

NumPy tutorial https://numpy.org/doc/stable/user/quickstart.html

```python
In [24]: np.ones(10)
Out[24]: array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])

In [25]: type(np.ones(10))
Out[25]: numpy.ndarray

In [26]: np.ones((10,3))
Out[26]:
array([[1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.],
       [1., 1., 1.]])

In [29]: # lists, tuples, dicts

In [32]: help(np.ones)


In [33]: np.ones?

In [44]: # for loop

In [45]: for k in l:
    ...:     print(l)
    ...:
[1, 2, 3]
[1, 2, 3]
[1, 2, 3]

In [46]: for k in l:
    ...:     print(k)
    ...:
1
2
3

In [49]: for k in range(10):
    ...:     print(k)
    ...:
0
1
2
3
4
5
6
7
8
9

In [54]: for k in 'abcd':
    ...:     print(k)
    ...:
a
b
c
d

In [55]: len('abc')
Out[55]: 3

In [56]: # python expression

In [57]: # lists

In [58]: l = [k for k in range(10)]

In [59]: l
Out[59]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [60]: [k for k in 'abcde']
Out[60]: ['a', 'b', 'c', 'd', 'e']

In [61]: # list of lists

In [62]: [(k,m) for k in range(3) for m in range(4)]
Out[62]:
[(0, 0),
 (0, 1),
 (0, 2),
 (0, 3),
 (1, 0),
 (1, 1),
 (1, 2),
 (1, 3),
 (2, 0),
 (2, 1),
 (2, 2),
 (2, 3)]

In [63]: # nested for loop

In [64]: [[k,m] for k in range(3) for m in range(4)]
Out[64]:
[[0, 0],
 [0, 1],
 [0, 2],
 [0, 3],
 [1, 0],
 [1, 1],
 [1, 2],
 [1, 3],
 [2, 0],
 [2, 1],
 [2, 2],
 [2, 3]]

In [65]: # nested for loop

In [66]: for k in range(3):
    ...:     for m in range(4):
    ...:         print([k,m])
    ...:
[0, 0]
[0, 1]
[0, 2]
[0, 3]
[1, 0]
[1, 1]
[1, 2]
[1, 3]
[2, 0]
[2, 1]
[2, 2]
[2, 3]

In [67]: # check your indentation for for-loops

In [68]: l
Out[68]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [69]: l[0]
Out[69]: 0

In [70]: l[1] + 1
Out[70]: 2

In [71]: # modify list elem-s

In [72]: l[3] = -10

In [73]: l
Out[73]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [74]: # appending elem-s to list

In [75]: l.append('abc')

In [76]: l.append(math.e)

In [77]: l
Out[77]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9, 'abc', 2.718281828459045]

In [78]: len(l)
Out[78]: 12

In [79]: list?
Init signature: list(self, /, *args, **kwargs)
Docstring:
list() -> new empty list
list(iterable) -> new list initialized from iterable's items
Type:           type
Subclasses:     _HashedSeq, StackSummary, SList, List, List, List, List, _ImmutableLineList, FormattedText, NodeList, ...

In [80]: l.pop()
Out[80]: 2.718281828459045

In [81]: l
Out[81]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9, 'abc']

In [82]: len(l)
Out[82]: 11

In [83]: l.pop()
Out[83]: 'abc'

In [84]: len(l)
Out[84]: 10

In [85]: l
Out[85]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [86]: a = l

In [87]: # now var "a" points to var "l"

In [88]: a == l
Out[88]: True

In [89]: a = l.copy()

In [90]: a == l
Out[90]: True

In [91]: a is ll
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-91-f1b42bb5e372> in <module>
----> 1 a is ll

NameError: name 'll' is not defined

In [92]: a is l
Out[92]: False

In [93]: a = l

In [94]: a is l
Out[94]: True

In [95]: b = l.copy() # b will be at new mem-y loc-n

In [96]: b is l
Out[96]: False

In [97]: b is a
Out[97]: False

In [98]: a
Out[98]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [99]: # modifying "l" modifies "a"

In [100]: a[0]=100

In [101]: a
Out[101]: [100, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [102]: l
Out[102]: [100, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [103]: a is l
Out[103]: True

In [104]: b
Out[104]: [0, 1, 2, -10, 4, 5, 6, 7, 8, 9]

In [105]: l.sort()

In [106]: # notice no output

In [107]: # "l" sorted

In [108]: l
Out[108]: [-10, 1, 2, 4, 5, 6, 7, 8, 9, 100]

In [109]: l.clear?
Docstring: L.clear() -> None -- remove all items from L
Type:      builtin_function_or_method

In [110]: l.extend?
Docstring: L.extend(iterable) -> None -- extend list by appending elements from the iterable
Type:      builtin_function_or_method

In [111]: print(l)
[-10, 1, 2, 4, 5, 6, 7, 8, 9, 100]

In [112]: l.extend([1,2,3])

In [113]: print(l)
[-10, 1, 2, 4, 5, 6, 7, 8, 9, 100, 1, 2, 3]

In [114]: l.append([1,2,3])

In [115]: print(l)
[-10, 1, 2, 4, 5, 6, 7, 8, 9, 100, 1, 2, 3, [1, 2, 3]]

In [116]: # tuples

In [117]: t = (1,) # single element tuple

In [118]: (1)
Out[118]: 1

In [119]: (1,)
Out[119]: (1,)

In [120]: (1,2,3,)
Out[120]: (1, 2, 3)

In [121]: [(-1,1), (1,1), (0,1)]
Out[121]: [(-1, 1), (1, 1), (0, 1)]

In [122]: # tuples are not mutable/ can't modify

In [123]: t[0]
Out[123]: 1

In [124]: t[0] = 0
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-124-51595a4035f3> in <module>
----> 1 t[0] = 0

TypeError: 'tuple' object does not support item assignment

In [125]: len(t)
Out[125]: 1

In [126]: new_t = (1,2,3,'apple', 'orange')

In [127]: new_t
Out[127]: (1, 2, 3, 'apple', 'orange')

In [128]: len(new_t)
Out[128]: 5

In [129]: for k in new_t: print(k);
1
2
3
apple
orange

In [130]: new_new_t = ((q,[l,m]) for q in range(5) for l in 'ab' for m in range(3))

In [131]: new_new_t
Out[131]: <generator object <genexpr> at 0x7f86951eeba0>

In [132]: # need to expand generator obj: tuple(new_new_t)

In [133]: tuple(new_new_t)
Out[133]:
((0, ['a', 0]),
 (0, ['a', 1]),
 (0, ['a', 2]),
 (0, ['b', 0]),
 (0, ['b', 1]),
 (0, ['b', 2]),
 (1, ['a', 0]),
 (1, ['a', 1]),
 (1, ['a', 2]),
 (1, ['b', 0]),
 (1, ['b', 1]),
 (1, ['b', 2]),
 (2, ['a', 0]),
 (2, ['a', 1]),
 (2, ['a', 2]),
 (2, ['b', 0]),
 (2, ['b', 1]),
 (2, ['b', 2]),
 (3, ['a', 0]),
 (3, ['a', 1]),
 (3, ['a', 2]),
 (3, ['b', 0]),
 (3, ['b', 1]),
 (3, ['b', 2]),
 (4, ['a', 0]),
 (4, ['a', 1]),
 (4, ['a', 2]),
 (4, ['b', 0]),
 (4, ['b', 1]),
 (4, ['b', 2]))

In [134]: t2 = tuple(new_new_t)

In [135]: t2
Out[135]: ()

In [136]: t2
Out[136]: ()

In [137]: tuple(new_new_t)
Out[137]: ()

In [138]: new_new_t = ((q,[l,m]) for q in range(5) for l in 'ab' for m in range(3))

In [139]: new_new_t = tuple(new_new_t)

In [140]: new_new_t
Out[140]:
((0, ['a', 0]),
 (0, ['a', 1]),
 (0, ['a', 2]),
 (0, ['b', 0]),
 (0, ['b', 1]),
 (0, ['b', 2]),
 (1, ['a', 0]),
 (1, ['a', 1]),
 (1, ['a', 2]),
 (1, ['b', 0]),
 (1, ['b', 1]),
 (1, ['b', 2]),
 (2, ['a', 0]),
 (2, ['a', 1]),
 (2, ['a', 2]),
 (2, ['b', 0]),
 (2, ['b', 1]),
 (2, ['b', 2]),
 (3, ['a', 0]),
 (3, ['a', 1]),
 (3, ['a', 2]),
 (3, ['b', 0]),
 (3, ['b', 1]),
 (3, ['b', 2]),
 (4, ['a', 0]),
 (4, ['a', 1]),
 (4, ['a', 2]),
 (4, ['b', 0]),
 (4, ['b', 1]),
 (4, ['b', 2]))

In [141]: new_new_t[0]
Out[141]: (0, ['a', 0])

In [142]: new_new_t[0][0]
Out[142]: 0

In [143]: new_new_t[0][1]
Out[143]: ['a', 0]

In [144]: new_new_t[0][1][0]
Out[144]: 'a'

In [145]: new_new_t[0][1][0] = 'c'

In [146]: new_new_t
Out[146]:
((0, ['c', 0]),
 (0, ['a', 1]),
 (0, ['a', 2]),
 (0, ['b', 0]),
 (0, ['b', 1]),
 (0, ['b', 2]),
 (1, ['a', 0]),
 (1, ['a', 1]),
 (1, ['a', 2]),
 (1, ['b', 0]),
 (1, ['b', 1]),
 (1, ['b', 2]),
 (2, ['a', 0]),
 (2, ['a', 1]),
 (2, ['a', 2]),
 (2, ['b', 0]),
 (2, ['b', 1]),
 (2, ['b', 2]),
 (3, ['a', 0]),
 (3, ['a', 1]),
 (3, ['a', 2]),
 (3, ['b', 0]),
 (3, ['b', 1]),
 (3, ['b', 2]),
 (4, ['a', 0]),
 (4, ['a', 1]),
 (4, ['a', 2]),
 (4, ['b', 0]),
 (4, ['b', 1]),
 (4, ['b', 2]))

In [147]: # dict

In [148]: d = {'a': 2}

In [149]: d
Out[149]: {'a': 2}

In [150]: d['a']
Out[150]: 2

In [151]: for k in d: print(k);
a

In [152]: # loops through keys in "d"

In [153]: for k in d: print(d[k]);
2

In [154]: # another indexing for lists and tuples

In [155]: l
Out[155]: [-10, 1, 2, 4, 5, 6, 7, 8, 9, 100, 1, 2, 3, [1, 2, 3]]

In [156]: l[-1]
Out[156]: [1, 2, 3]

In [157]: l[-2]
Out[157]: 3

In [158]: # slicing

In [159]: l[:5]
Out[159]: [-10, 1, 2, 4, 5]

In [160]: l[5:]
Out[160]: [6, 7, 8, 9, 100, 1, 2, 3, [1, 2, 3]]

In [161]: exit()
➜  ~
➜  ~
➜  ~ import skimage.io
zsh: command not found: import
➜  ~ ipython
Python 3.6.9 |Anaconda, Inc.| (default, Jul 30 2019, 13:42:17)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.8.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import skimage.io.imread as imread
---------------------------------------------------------------------------
ModuleNotFoundError                       Traceback (most recent call last)
<ipython-input-1-618de0991a09> in <module>
----> 1 import skimage.io.imread as imread

ModuleNotFoundError: No module named 'skimage.io.imread'

In [2]: from  skimage.io import imread

In [3]: imread?

In [4]: # if , elif, else

In [5]: if len(l)>100:
   ...:     print('1')
   ...: elif len(l)>1000:
   ...:     print('2)
  File "<ipython-input-5-892a7dc63519>", line 4
    print('2)
             ^
SyntaxError: EOL while scanning string literal


In [6]: if len(l)>100:
   ...:     print('1')
   ...: elif len(l)>1000:
   ...:     print('2')
   ...: else:
   ...:     print('3')
   ...:
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-6-c06d6095ec86> in <module>
----> 1 if len(l)>100:
      2     print('1')
      3 elif len(l)>1000:
      4     print('2')
      5 else:

NameError: name 'l' is not defined

In [7]: l = [k for k in range(10)]

In [8]: l
Out[8]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

In [9]: if len(l)>20:
   ...:     print('1')
   ...: elif len(l)>30:
   ...:     print('2')
   ...: else:
   ...:     print('3')
   ...:
3

In [10]: exit()      
```
