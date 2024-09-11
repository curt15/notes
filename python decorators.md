Links: [[PYTHON ]] - [[PROGRAMMING]]
Rel: [[python functions]]; [[property]] - @property is a decorator
Ref: 
- https://stackoverflow.com/questions/308999/what-does-functools-wraps-do

```from functools import wraps```

--- 
### decorators
e.g. flask routes **@app.route** wraps the view function so that when '/route/' is called, your template is rendered
```py
@app.route('/about')
def about():
	return render_template('about.html')
```
```py

def manip()
```

--- 

```py
>>> from functools import wraps
>>> def manip(func):
...     @wraps(func)
...     def inner(*args, **kwargs):
...             func()
...             print('This also executes')
...             return 
...     return inner
... 
>>> def hello():
...     print('hello world')
... 
>>> hello()
hello world
>>> 
>>> @manip
... def hello():
...     print('hello world')
... 
>>> hello()
hello world
This also executes
>>> 
```

--- 

syntactic sugar
metaprogramming because code modifying code at run-time

functions are objects too (names with bound attributes)

higher-order functions - take functions as arguments
```py
def execute_this(func, *args):
	return func(*args)


>>> execute_this(print, 'Hello World')
'Hello World'

```


A decorator is a high-order function that (wraps and) returns another function:

```from functools import wraps```

```py
def add_two(func): #expects a function argument
	@wraps(func) # passes metadata through wrapper
	def inner(*args, **kwargs):
		r = func(*args, **kwargs)
		return r + 2
	return inner #returns the wrapper (w/ func.__name__, __module__, __doc__)

def prod_five():
	return 5
	

prod_seven = add_two(prod_five) # new function, same as:

@add_two
def prod_five():
	return 5		
```

wrappers call top-bottom and execute function -> bottom -> top
```py
def mod_seven(func):
	@wraps(func)
	def wrapper(*args, **kwargs):
		return func(*args, **kwargs) % 7
	return wrapper

@mod_seven
@add_two
def prod_five():
	return 5

# -> mod_seven(add_two(prod_five))()
# -> outputs: 0

@add_two
@mod_seven
def prod_five():
	return 5

# -> add_two(mod_seven(prod_five))()
# -> outputs: 5 


		
```

more complex example:
```py
def wrap_in_x(func):
    def inner(*args, **kwargs):
        print("x" * 30)
        func(*args, **kwargs)
        print("x" * 30)
    return inner


def wrap_in_y(func):
    def inner(*args, **kwargs):
        print("y" * 30)
        func(*args, **kwargs)
        print("y" * 30)
    return inner


@wrap_in_x
@wrap_in_y
def xy_wrap(msg):
    print(msg)


>>> xy_wrap("Hello World!w")

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
yyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
Hello World!
yyyyyyyyyyyyyyyyyyyyyyyyyyyyyy
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```
so calling xy_wrap() calls wrap_in_x -> wrap_in_y -> xy_wrap -> return

wrap_in_x -> print("x" \* 30) -> func(\*args, \*\*kwargs), where func is wrap_in_y ->
wrap_in_y -> print("y" \* 30) -> func(\*args, \*\*kwargs), where func is xy_wraps ->
xy_wraps -> print("Hello World!") -> xy_wraps has now returned (competed all statements), so
wrap_in_y -> print("y" \* 30) -> wrap_in_y now has returned, so
wrap_in_x -> print("x" \* 30) -> returned


--- 


decorate methods simply by taking self into account
```py
def add_two(mtd):
	def wrapper(self, *args, **kwargs):
		return mtd() + 2
	return wrapper
```


--- 

use decorators for debugging 

```py
import time
from functools import wraps

def timeit(func):
	"""Decorator to time a function """
	@wraps(func)
	def time_wrapper(*args, **kwargs):
		start = time.time()
		function = func(*args, **kwargs)
		end = time.time()
		total = end - start

		print(f'func:{func.__name__} args:{[args, kwargs]} took: {total} s')
		return function
	return time_wrapper
```

```py
from functools import partial, wraps

def debug(func=None, *, prefix=''):
	""" """
	if func is None:
		return partial(debug, prefix=prefix)

	msg = prefix + func.__qualname__
	@wraps(func)
	def wrapper(*args, **kwargs):
		print(msg)
		return func(*args, **kwargs)
	return wrapper
```

--- 
etc

```py
def rename(newname):
	""" a simple generic decorator to dynamically re-name a function """
	def dec(f):
		f.__name__ = newname
		return f
	return dec
```



--- 

References:
- https://gist.github.com/Zearin/2f40b7b9cfc51132851a
- https://realpython.com/primer-on-python-decorators
- https://www.programiz.com/python-programming/decorator#decorating
- 