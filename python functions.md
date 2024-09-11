Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python decorators]]
Tags: #public 

--- 

### functions

**\*args **
- when unsure how many (additional) arguments might be passed into your function
```py
def add_exclaim(*args)->list:
	fin = []
	for a in args:
		if not type(a) == str:
			a = str(a)
		a += '!'
		fin.append(a)	
	return fin


>>> 
>>> my_strs = ['this', 'is', 'rocket', 'science', 2]
>>> add_exclaim(*my_strs)
['this!', 'is!', 'rocket!', 'science!', '2!']
```
- when ensuring everything passes through your super() or @exampdec,
- can un-pack **lists** (iterables) into function calls with **\***
```py
>>> def examp(x,y): pass
>>> li = ['this', 'that']
>>> examp(*li)
>>> # equivelant to: 
>>> examp('this', 'that')
>>> # which would otherwise fail without unpacking, because it's a single list
>>> examp(['this', 'that'])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: examp() missing 1 required positional argument: 'y'
```
```py
>>> 
>>> # or get something weird you didn't want...
>>> # with unpacking into a *args definition (above)
>>> add_exclaim(*my_strs)
['this!', 'is!', 'rocket!', 'science!', '2!']
>>> # ... without unpacking you get:
>>> add_exclaim(my_strs)
>>> ["['this', 'is', 'rocket', 'science', 2]!"]
>>> # oops...
>>> # --> 
>>> def add_exclaim(*args)->list:
	fin = []
	if len(args) == 1 and type(args[0]) == list:
		args = args[0]
	for a in args:
		if not type(a) == str:
			a = str(a)
		a += '!'
		fin.append(a)	
	return fin
>>> 
>>> x = ['this!', 'is!', 'rocket!', 'science!', '2!']
>>> add_exclaim(x)
['this!!', 'is!!', 'rocket!!', 'science!!', '2!!']
>>> add_exclaim(*x)
['this!!', 'is!!', 'rocket!!', 'science!!', '2!!']
>>> # ^^ very nice!
```
->


--- 

**\*kwargs**
- key-word arguments; will fail if not named explicitly when calling the function/method
- any argument pre-defined (e.g. ```def func(y=None): pass```) is a kwarg. This means, you *have* to call func() with y as ```func(y="this")``` aka now fail on ```func("this")```, which as a positional argument by default in ```def func(y): pass``` would accept ```func("this")``` as y regardless. P.s. ```func()``` works just fine as y is happy with None.
- anything after \* in a function definition is now a kwarg (even if it's not pre-defined), ```def examp(*, x, y=None): pass``` requires x and y to make a correct call ```examp(x='this', y='that')```, where ```examp('this', y='that')``` fails, and again ```examp(x='this')``` works fine as y is still None unless otherwise stated when called. 
- you cannot define a positional argument after a pre-defined kwarg e.g. ```def func(y=None, z): pass``` is a [[SyntaxError]]...
- you can unpack **dict**(-likes) with \*\* to provide kwargs (nice!):
```py
>>> def examp(*, x, y=None): pass
>>> mydic = {'x': 'this', 'y': 'that'}
>>> examp(**mydic)
>>> # is equivelant to: 
>>> examp(x='this', y='that'))
>>> # note: x and y are kwargs only!
>>> examp('this', 'that')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: examp() takes 0 positional arguments but 2 were given
>>> 
```

--- 

https://betterprogramming.pub/how-to-define-function-parameters-as-positional-keyword-or-both-in-python-8753ca2ac5ca

```py
def blah(x,/,y,*,z):
	pass
```