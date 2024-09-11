Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]; [[builtins]]
Ref: 
Tags: #public 

--- 

vars(obj)
- returns the \_\_dict\_\_ attribute if provided an obj
- otherwise, if called empty, acts like [[locals]]()

```py
>>> def myfunc():
...     x = 'local var'
...     print(vars())
...     return None
... 
>>> myfunc()
{'x': 'local var'}
```

```py
>>> vars()
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, 'myfunc': <function myfunc at 0x1051285e0>}
```

```py

>>> class MyThing:
...     clsvar = 'CLSVAR'
...     def __init__(self):
...             self.instvar = 'INSTVAR'
... 
>>> vars(MyThing)
mappingproxy({'__module__': '__main__', 'clsvar': 'CLSVAR', '__init__': <function MyThing.__init__ at 0x10cdff790>, '__dict__': <attribute '__dict__' of 'MyThing' objects>, '__weakref__': <attribute '__weakref__' of 'MyThing' objects>, '__doc__': None})
>>> vars(MyThing())
{'instvar': 'INSTVAR'}
```