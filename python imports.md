Links: [[ INDEX ]] - [[PYTHON]]
Rel: [[import this]]
Ref: 
Tags: #public 

--- 

- [[#namespace]]
- [[#variables]]
- [[#imports modules packages]]
- [[#import syntax]]

--- 

#### [[namespace]]

a **namespace** is an abstract container that holds logically grouped unique identifiers (and the value of the things that they reference) by a name.

When you invoke the Python interpreter inside your shell ([[command-line interface]]), you can see that your prompt changes to ```>>>```. You have stepped into a new *environment* with ```python3``` - a special namespace where you can directly execute instructions written in Python.

```sh
$ python3
Python 3.9.6 (v3.9.6:db3ff76da1, Jun 28 2021, 11:49:53) 
[Clang 6.0 (clang-600.0.57)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
```py
>>> print("Hello World!")
Hello World!
```

^^ in ```print("Hello World!")``` we've ***called*** the  (built-in Python) ***function*** ```print``` by closing parenthesis (e.g. ```func()```) around an ***argument***, "Hello World!".  

--- 
#### variables

We can set values to ***variables*** with the ```=``` operator
```py
>>> x = 'some text'
>>> # define a str variable
>>> # print it
>>> print(x)
some text
```
and check equivalence with the ```==``` operator
```py
>>> myvar == mv2
True
```

make sure you don't overwrite **builtins** with the power of ```=```
```py
>>> print("hello world")
hello world
>>> print = "this is bad"
>>> print('why?')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object is not callable
```

**Object-Oriented Programming (OOP) ~= "Everything is an [Object](https://docs.python.org/3/reference/datamodel.html#object.__hash__)"**

```TypeError: 'str' object is not callable```
```'str' object is not callable```
```'str' object```
```object```
...

--- 

#### dir(\[ object \]) [docs](https://docs.python.org/3/library/functions.html#dir)
called empty, returns a *list* of names in the current local scope or attributes of the object given as optional argument:

```py
>>> dir()

['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__']
```

anything that you define (or import), then becomes part of your scope.
```py
>>> x = 'some text'
>>> dir() # see at the very end ----------------------------------------------------------> that our x was appended!
['__annotations__', '__builtins__', '__doc__', '__loader__', '__name__', '__package__', '__spec__', 'x']
>>> x
'some text'
>>> # that itself, as an object, has a scope...
>>> dir(x)
['__abs__', '__add__', '__and__', '__bool__', '__ceil__', '__class__', '__delattr__', '__dir__', '__divmod__', '__doc__', '__eq__', '__float__', '__floor__', '__floordiv__', '__format__', '__ge__', '__getattribute__', '__getnewargs__', '__gt__', '__hash__', '__index__', '__init__', '__init_subclass__', '__int__', '__invert__', '__le__', '__lshift__', '__lt__', '__mod__', '__mul__', '__ne__', '__neg__', '__new__', '__or__', '__pos__', '__pow__', '__radd__', '__rand__', '__rdivmod__', '__reduce__', '__reduce_ex__', '__repr__', '__rfloordiv__', '__rlshift__', '__rmod__', '__rmul__', '__ror__', '__round__', '__rpow__', '__rrshift__', '__rshift__', '__rsub__', '__rtruediv__', '__rxor__', '__setattr__', '__sizeof__', '__str__', '__sub__', '__subclasshook__', '__truediv__', '__trunc__', '__xor__', 'as_integer_ratio', 'bit_length', 'conjugate', 'denominator', 'from_bytes', 'imag', 'numerator', 'real', 'to_bytes']
```

there's a whole lot available to see without importing anything...
```py
>>> dir(__builtins__)

['ArithmeticError', 'AssertionError', 'AttributeError', 'BaseException', 'BlockingIOError', 'BrokenPipeError', 'BufferError', 'BytesWarning', 'ChildProcessError', 'ConnectionAbortedError', 'ConnectionError', 'ConnectionRefusedError', 'ConnectionResetError', 'DeprecationWarning', 'EOFError', 'Ellipsis', 'EnvironmentError', 'Exception', 'False', 'FileExistsError', 'FileNotFoundError', 'FloatingPointError', 'FutureWarning', 'GeneratorExit', 'IOError', 'ImportError', 'ImportWarning', 'IndentationError', 'IndexError', 'InterruptedError', 'IsADirectoryError', 'KeyError', 'KeyboardInterrupt', 'LookupError', 'MemoryError', 'ModuleNotFoundError', 'NameError', 'None', 'NotADirectoryError', 'NotImplemented', 'NotImplementedError', 'OSError', 'OverflowError', 'PendingDeprecationWarning', 'PermissionError', 'ProcessLookupError', 'RecursionError', 'ReferenceError', 'ResourceWarning', 'RuntimeError', 'RuntimeWarning', 'StopAsyncIteration', 'StopIteration', 'SyntaxError', 'SyntaxWarning', 'SystemError', 'SystemExit', 'TabError', 'TimeoutError', 'True', 'TypeError', 'UnboundLocalError', 'UnicodeDecodeError', 'UnicodeEncodeError', 'UnicodeError', 'UnicodeTranslateError', 'UnicodeWarning', 'UserWarning', 'ValueError', 'Warning', 'ZeroDivisionError', '_', '__build_class__', '__debug__', '__doc__', '__import__', '__loader__', '__name__', '__package__', '__spec__', 'abs', 'all', 'any', 'ascii', 'bin', 'bool', 'breakpoint', 'bytearray', 'bytes', 'callable', 'chr', 'classmethod', 'compile', 'complex', 'copyright', 'credits', 'delattr', 'dict', 'dir', 'divmod', 'enumerate', 'eval', 'exec', 'exit', 'filter', 'float', 'format', 'frozenset', 'getattr', 'globals', 'hasattr', 'hash', 'help', 'hex', 'id', 'input', 'int', 'isinstance', 'issubclass', 'iter', 'len', 'license', 'list', 'locals', 'map', 'max', 'memoryview', 'min', 'next', 'object', 'oct', 'open', 'ord', 'pow', 'print', 'property', 'quit', 'range', 'repr', 'reversed', 'round', 'set', 'setattr', 'slice', 'sorted', 'staticmethod', 'str', 'sum', 'super', 'tuple', 'type', 'vars', 'zip']
```
```py
>>> dir(__package__)
['__bool__', '__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
```
```py
>>> dir(__name__)
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'removeprefix', 'removesuffix', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```
```py
>>> dir(__loader__)
['_ORIGIN', '__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'create_module', 'exec_module', 'find_module', 'find_spec', 'get_code', 'get_source', 'is_package', 'load_module', 'module_repr']
```
```py
>>> dir(__doc__)
['__bool__', '__class__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__']
```
```py
>>> dir(__annotations__)
['__class__', '__class_getitem__', '__contains__', '__delattr__', '__delitem__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__ior__', '__iter__', '__le__', '__len__', '__lt__', '__ne__', '__new__', '__or__', '__reduce__', '__reduce_ex__', '__repr__', '__reversed__', '__ror__', '__setattr__', '__setitem__', '__sizeof__', '__str__', '__subclasshook__', 'clear', 'copy', 'fromkeys', 'get', 'items', 'keys', 'pop', 'popitem', 'setdefault', 'update', 'values']
```

^^ you don't need to worry about all this off the jump. Notice that you can see the function ```'print'``` in the returned [[list]] when calling ```dir(__builtins__)```.

Try **calling** another **function** found in that list of [[builtins]], ```'help'```: 

```py
>>> help(print)
```
```
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
(END)
```
press **esc** to exit the documentation -> 
```py
>>> 
```




--- 

## imports, modules, packages, libraries 

a **library** is ... 

when you get to naming organized code that becomes larger than **modules** and **packages** (and contain them!).

The [[python standard library]]  provides many modules and packages available by e.g. ```import os``` and additional modules, packages, and libraries can be installed (see: [[python 3rd party packages]]) by using [[pip]] (e.g. ```pip install package-name```). 

--- 

A python **module** is generally (colloquially) used to define a single **.py** file (and all the code within), but a **module** can additionally be a directory of files (which can contain submodules or recursively, subpackages, by using additional nested directories). 

Technically, a **package** is a Python module with an **\_\_path\_\_** attribute ([source - docs ](https://docs.python.org/3/glossary.html#term-package)), achieved by adding an (at a minimum and commonly so, empty)  **\_\_init\_\_.py** file to the directory, e.g. : 

We have a directory **hello/** and inside of it, a Python module: **world.py**. 

**hello/world.py**
```py
# world.py

if __name__ == '__main__':
	print('hello world')
```
```py
% ls hello/ # listing the files in folder hello/
world.py
% python3
>>> # at the python interpreter...
>>> import hello
>>> hello.__path__
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: module 'hello' has no attribute '__path__'
>>> exit()
% # back in our OS-es shell
```
-> **hello/\_\_init\_\_.py**
```py
% touch hello/__init__.py # creating an empty file
% ls hello
__init__.py world.py
% python3
>>> # ...
>>> import hello
>>> hello.__path__
['/users/alice/prog/hello']
```

--- 


--- 

**if \_\_name\_\_ == '\_\_main\_\_':**

```py
if __name__ == '__main__':
	my_function_call()
```

What is this (commonly used pattern in Python) doing?

```py
% python3
>>> import hello
>>> hello.__name__
'hello'
>>> __name__
'__main__'
>>> exit()
```
```py
% python3 hello/world.py
Hello World
```

When calling **world.py** directly (e.g. like immediately above, as a script), the global variable ```__name__``` *is actually now* ```'__main__'```, according to the ```python3``` interpreter (and world.py). Look again above where the variable ```__name__``` is ```'__main__'``` and  ```hello.__name__``` is ```'hello'``` when directly at the Python interpreter ```>>> ```.

The call to ```print('hello world')``` occurs when we run **```python3 hello/world.py```** because, in this case, our **if statement** asking if ```__name__``` is ```'__main__'```returns ```True```).


Next, see what happens when we ```import world``` instead of running world.py itself: 

```py
% echo "import world" > hello/test1.py # creating test1.py and writing to it
% ls hello
__init__.py world.py test1.py
% python3 hello/test1.py
% # ... 
```

```print('hello world')``` *doesn't* get run, why? 

hello.py 's \_\_name\_\_ is again ```'hello'``` when imported into test1.py, and  ```__name__``` is now ```'__main__'``` for test1.py because *now it's being called directly* !

Finally, what if **world.py** instead looked like this:

```py
print('hello world')

if __name__ == '__main__':
	print('hello again!')
```
```bash
% python3 hello/test1.py
hello world
% # ...
% python3 hello/world.py
hello world
hello again!
```

```print('hello world')``` ***does* get called** when running ```python3 hello/test1.py```, **why?**

Anytime you make an ```import``` in Python the entire module is run as it's being pulled into memory regardless what is being imported from it, meaning, where ```print('hello again!')``` isn't being run because it's under  ```if __name__ == '__main__':```, which is ```False``` in this case, it doesn't get called. ```print('hello world')```, outside of ```if __name__ == '__main__':``` or a function or class definition, like it is in **world.py**, will be called on ```import```.

```py
>>> from os import getcwd
>>> getcwd()
'/users/alice/prog'
```
^^ doesn't save you overhead, etc. as regardless *all of* the standard [[os]] module is read in, meaning, it doesn't save you memory / compile time compared to: 
```py
>>> import os
>>> os.getcwd()
'/users/alice/prog'
```

Why is this important?
- (1) It's far more explicit to ```import os``` and ```os.getcwd()```, rather than using ```from os import getcwd``` and ```getcwd()```, especially when using such a common function from such a common part of the [[python standard library]].
- (2) You don't always *normally* want things like ```print('hello world')``` to be called when you're making an import. This is why it's commonplace to put anything that you want to be called when running a .py module directly as a script within an ```if __name__ == '__main__':``` statement at the bottom of the file. 

--- 
### import syntax

```py
```

--- 

https://realpython.com/python-import/

from . import africa  # relative import
from world import africa  # absolute import

import pandas as pd  # bind module to local name

--- 

-> [[python packages]]

