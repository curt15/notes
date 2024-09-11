Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: https://docs.python.org/3/library/types.html

```import types```

--- 

types.FunctionType
- uncalled function (includes 'Example.mymethod')

types.MethodType
- uncalled user created instance method
```py
>>> class MyClass:
...     def fake(self):
...             return ''
... 
>>> isinstance(MyClass().fake, types.MethodType)
True
>>> isinstance(MyClass.fake, types.MethodType)
False
```

types.ModuleType
- a module
```py
>>> import types
>>> isinstance(types, types.ModuleType)
True
```

types.MethodWrapperType
- bound methods of some built-in data types and base classes. 
```py
>>> import types
>>> class MyClass:
...     pass
... 
>>> isinstance(MyClass().__str__, types.MethodWrapperType)
True
```


