Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]; [[builtins]]
Ref: 
Tags: #public 

--- 

Use isinstance(type, obj) -> bool,
similar to if type(obj) == type:

```py
>>> isinstance('this definite string', str)
True
>>> isinstance('this definite string', int)
False
>>> class MyThing:
...     pass
... 
>>> x = MyThing()
>>> isinstance(x, MyThing)
True
```