Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: 
Ref: 
Tags: #public 

--- 

## objects

```py
#test.py

class Examp:
	pass

```
```py
>>> from test import Examp
>>> dir(Examp)
['__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__', '__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']

>>> e = Examp()
>>> e.__dict__
{}
```

--- 

#### object definition
#### -> local MRO (method resolution order)

```py
from collections import OrderedDict

class Examp(type):
```
\_\_prepare\_\_()
```py
	_dict = OrderedDict()
	
	@classmethod
	def __prepare__():
		"""
		3.7 docs:
		If the metaclass has no __prepare__ attribute,
		then the class namespace is initialised as an empty ordered mapping.
		"""
        
		return _dict
```
\_\_new\_\_(cls, name, bases, clsdict)
```py
	def __new__(cls, name, bases, clsdict):
		"""
		Use when you need to control the creation of a new instance.
        
		is the first step in instance creation. It's called first, and is
		responsible for returning a new instance of your class.
        
        is static class method.

		In general, you shouldn't need to override __new__ unless you're
		subclassing an immutable type like str, int, unicode, or tuple.

		3.7 docs:
		is intended mainly to allow subclasses of immutable types (like int, str, or tuple)
		to customize instance creation.

		It is also commonly overridden in custom metaclasses in order to customize class creation.

		the object provided as the namespace parameter is copied to
		a new ordered mapping and the original object is discarded.

		The new copy is wrapped in a read-only proxy, which becomes
		the __dict__ attribute of the class object.
		"""

		pass
```
\_\_init\_\_(self, )
```py
	def __init__(self, ):
		"""
		Use when you need to control the initialization of a new instance.

		doesn't return anything; it's only responsible for initializing
		the instance after it's been created.

		is instance method.

		3.7 docs:
		called after the instance has been created (by __new__()), but before it is returned to the caller.

		The arguments are those passed to the class constructor expression.
		"""
        
		pass
```
__repr__()
```py
	def __repr__(self):
		"""
		Called by the repr() built-in function to compute the
		“official” string representation of an object.

		If at all possible, this should look like a valid Python expression
		that could be used to recreate an object with the same value (given an appropriate environment).

		If this is not possible, a string of the form <...some useful description...> should be returned.

		The return value must be a string object.

		If a class defines __repr__() but not __str__(),
		then __repr__() is also used when an “informal” string representation
		of instances of that class is required.

		This is typically used for debugging, so it is important that the representation is
		information-rich and unambiguous.
		"""
        
		pass
```

--- 

other typical dunder/magic methods:
```py
	def __str__(self):
		""" informal string representation """
		pass

	def __eq__(self, other):
		pass

	def __hash__(self):
		pass
	
	def __call__(self):
		pass
```
\_\_call\_\_
```py
class MyThing:
	def __init__(self):
		print('initialized!')
	def __call__(self):
		print('instance call happened!')
```
```py
>>> a = MyThing()
initialized!
>>> a()
instance call happened!
```

--- 

... to cleanly get custom metaclass \_\_dir\_\_ data:
```py
attrs = [g for g in dir(ClassName) if g[0] != '_' and g[-1] != '_']

attrs = [g for g in inspect.getmembers(Cards)]

attrs = [g for g in self.__dict__.items()]

attrs = inspect.getmembers(self, lambda a: not(inspect.isroutine(a)))

return [a for a in attributes if not(a[0].startswith('__') and a[0].endswith('__'))]
```

--- 

#### super() and meta attribute flow
```py
class Example:

	OUT_EX = '!ATTR in Example def'
	
	def __init__(self);
		self.IN_EX = '!ATTR in Example.__init__'
```

```py
>>> dir(Example)
['OUT_EX',
	'__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__',

	'__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

	'__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__',

	'__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']


>>> vars(Example)

	{'__module__': '__main__',

	'OUT_EX': '!ATTR in Example def',

	'__init__': <function Example.__init__ at 0x10bf961e0>, '__dict__': <attribute '__dict__' of 'Example' objects>,

	'__weakref__': <attribute '__weakref__' of 'Example' objects>, '__doc__': None}


>>> Example.__dict__

	{'__module__': '__main__', 'OUT_EX': '!ATTR in Example def',

	'__init__': <function Example.__init__ at 0x10bf961e0>, '__dict__': <attribute '__dict__' of 'Example' objects>,

	'__weakref__': <attribute '__weakref__' of 'Example' objects>, '__doc__': None}
	


>>> import inspect
>>> inspect.signature(Example)
()



>>> e = Example()

>>> dir(e)
['IN_EX', 'OUT_EX',

'__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__',

'__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

'__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__',

'__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']


>>> vars(e)
{'IN_EX': '!ATTR in Example.__init__'}


>>> e.__dict__
{'IN_EX': '!ATTR in Example.__init__'}
```


```py
class Child(Example):

	OUT_CHILD = '!ATTR in Child def'

	def __init__(self):
		self.IN_CHILD = '!ATTR in Child.__init__'
```

dir() += OUT_EX, BUT NOT in vars() or .__dict__

```py
>>> dir(Child)

['OUT_CHILD', 'OUT_EX',

'__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__',

'__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

'__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__',

'__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']



>>> vars(Child)

{'__module__': '__main__',

'OUT_CHILD': '!ATTR in Child def', '__init__': <function Child.__init__ at 0x10bf96268>,

'__doc__': None}



>>> Child.__dict__
	{'__module__': '__main__',

	'OUT_CHILD': '!ATTR in Child def', '__init__': <function Child.__init__ at 0x10bf96268>,

	'__doc__': None}


>>> import inspect
>>> inspect.signature(Child)
()
```

```py
>>> c = Child()


>>> dir(c)

['IN_CHILD', 'OUT_CHILD', 'OUT_EX',

'__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__',

'__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

'__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__',

'__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']



>>> vars(c)

{'IN_CHILD': '!ATTR in Child.__init__'}



>>> c.__dict__

{'IN_CHILD': '!ATTR in Child.__init__'}

```

--- 

#### metaclass definition:

```py
class MyMeta(type):

	def __new__(cls, name, bases, attrs):

		clsobj = super().__new__(cls, name, bases, attrs)

		setattr(clsobj, 'FRM_MTA', '!ATTR in MyMeta.__new__') # only shows in children classes...

		return clsobj

```

```py
>>> dir(MyMeta)

['__abstractmethods__', '__base__', '__bases__', '__basicsize__', '__call__',

'__class__', '__delattr__', '__dict__', '__dictoffset__', '__dir__', '__doc__', '__eq__', '__flags__',

'__format__', '__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

'__instancecheck__', '__itemsize__', '__le__', '__lt__', '__module__', '__mro__', '__name__', '__ne__',

'__new__', '__prepare__', '__qualname__', '__reduce__', '__reduce_ex__', __repr__', '__setattr__',

'__sizeof__', '__str__', '__subclasscheck__', '__subclasses__', '__subclasshook__',

'__text_signature__', '__weakrefoffset__', 'mro']



>>> vars(MyMeta)

{'__module__': '__main__',

'__new__': <staticmethod object at 0x10be64cf8>,

'__doc__': None}



>>> MyMeta.__dict__

{'__module__': '__main__',

'__new__': <staticmethod object at 0x10be64cf8>,

'__doc__': None}


>>> import inspect
>>> inspect.signature(MyMeta)
(name, base, attrs)


```

#### metaclass inheritance

```py
class ExampMetaHeir(metaclass=MyMeta):
	pass
```
```py
>>> dir(ExampMetaHeir)

['FRM_MTA',

'__class__', '__delattr__', '__dict__', '__dir__', '__doc__', '__eq__', '__format__',

'__ge__', '__getattribute__', '__gt__', '__hash__', '__init__', '__init_subclass__',

'__le__', '__lt__', '__module__', '__ne__', '__new__', '__reduce__', '__reduce_ex__',

'__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__']



>>> vars(ExampMetaHeir)

{'__module__': '__main__',

'__dict__': <attribute '__dict__' of 'ExampMetaHeir' objects>,

'__weakref__': <attribute '__weakref__' of 'ExampMetaHeir' objects>,

'__doc__': None,

'FRM_MTA': '!ATTR in MyMeta.__new__'}



>>> ExampMetaHeir.__dict__

{'__module__': '__main__',

'__dict__': <attribute '__dict__' of 'ExampMetaHeir' objects>,

'__weakref__': <attribute '__weakref__' of 'ExampMetaHeir' objects>,

'__doc__': None,

'FRM_MTA': '!ATTR in MyMeta.__new__'}



>>> inspect.signature(ExampMetaHeir)
()

```


#### meta - append a class method

```py
class A:
	def __init__(self):
		pass

	def func(self):
		print('func derived from A')

class B:
	def __init__(self):
		pass

	def func(self):
		print('func derived from B')

class C(B,A):
	def __init__(self):
		super().__init__()



def append_cls_method(cls, name):
	def method(self):
		print(f'result from method {name}')

	method.__name__ = name
	return setattr(cls, name, method)

append_cls_method(A, 'new_func')


>>> c = C()
>>> c.func() 
'func derived from B'

>>> a = A()
>>> a.func()
'func derived from A'



>>> a.new_func()
'result from new_func'
```