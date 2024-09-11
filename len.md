Links: [[PYTHON]] - [[PROGRAMMING]]
Ref: [[python standard library]]; [[builtins]]

--- 

len() returns the length of an iterable (or the result of \_\_len\_\_)
```py
>>> len('this string is 36 chars long, right?')
36
>>> len(['this', 'has', 4, 'items'])
4
>>> len({'this':1, 'has':2, 4:3, 'items':4})
4
>>> class MyThing:
...     def __len__(self):
...             return 42
... 
>>> x = MyThing()
>>> len(x)
42
>>> len(500)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: object of type 'int' has no len()
```