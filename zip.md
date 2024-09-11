Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]
Ref: 
Tags: #public 

--- 
#### zip()
```py
>>> x = [1,2,3,4]
>>> y = [7,8,3,2]
>>> z = ['a','b','c','d']

>>> for a,b in zip(x,y):
...     print(a,b)
... 
1 7
2 8
3 3
4 2

# [print(x,y,z) for x,y,z in zip(x,y,z)] # same result
```
-> 2 lists into a **dict**
```py
>>> names = ['Bill', 'Chris', 'Abe', 'Tim']
>>> ages = [99,56,24,87]
>>> nameAges = dict(zip(name, ages))
>>> print(nameAges)
{'Bill': 99, 'Chris': 56, 'Abe': 24, 'Tim': 87}
```