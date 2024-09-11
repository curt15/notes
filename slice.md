Links: [[PYTHON]] - [[PROGRAMMING]]
Ref: [[python standard library]]; [[builtins]]

--- 
slice() -> 
```py
>>> l = ['c', 'd', 'e', 'f', 'g', 'h']
>>> l[1:2]
['d']
>>> l[slice(1,2,None)]
['d']
>>> l[slice(1,None,None)]
['d', 'e', 'f', 'g', 'h']
>>> l[1:]
['d', 'e', 'f', 'g', 'h']
>>> 
>>> s = 'this is my fancy string'
>>> s[1:2]
'h'
```