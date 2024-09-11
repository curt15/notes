Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: 
Ref: 
Tags: #public 

--- 

an empty dict() == None
```py
>>> d = {}
>>> if d:
...     print(x)
... 
>>> if d:
...     print('hello')
... 
>>> if dict():
...     print('why')
... 
```

dict.items()
returns a collection of tuples
```py
>>> d = {'d':3, 'e': 4}
>>> d.items()
dict_items([('d', 3), ('e', 4)])
>>> for i in d.items():
...     print(i)
... 
('d', 3)
('e', 4)
>>> type(d.items())
<class 'dict_items'>
```

accessing values
```py
>>> d = {'a':1, 'b':2}
>>> d['a']
1
>>> d.get('a')
1
>>> d['c']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'c'
>>> d.get('c')
>>> print(d.get('c'))
None
```