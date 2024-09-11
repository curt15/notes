Links: [[PYTHON]] - [[PROGRAMMING]]

--- 

cannot change list items while looping over them:
```py
>>> l = ['a','b','c']
>>> l[1] = 'b2'
>>> l
['a', 'b2', 'c']
>>> for i in l:
...     i = i+'2'
... 
>>> l
['a', 'b2', 'c']
```

--- 
list.insert(index, item)
```py
>>> l = ['a','c','d']
>>> l.insert(1, 'b')
>>> print(l)
['a', 'b', 'c', 'd']
```

list.remove(obj)

--- 
list.copy()

--- 
list indexing

```py
>>> l = [1,2,3,4,5,6,7,8,9,10]
>>> l[-1]
10
>>> l[-2]
9
>>> l[0]
1
```

list slicing 

```py
>>> l = [1,2,3,4,5]
>>> len(l)
5
>>> l[1:]
[2, 3, 4, 5]
```

--- 

-> dict comprehensions...

```py
>>> l1 = [1,2,3,4]
>>> l2 = ['a','b','c','d']
>>> 
>>> d = {x:y for x in l1 for y in l2}
>>> d
{1: 'd', 2: 'd', 3: 'd', 4: 'd'}
>>> # hmmm....
>>> 
>>> d = {x:l2[i] for i,x in enumerate(l1)}
{1: 'a', 2: 'b', 3: 'c', 4: 'd'}
>>> # !!!
```

--- 

-> list unpacking
```py
>>> l = [[1,2],[3,4]]
>>> for i in l:
...     x, y = i
...     print(x)
...     print(y)
... 
1
2
3
4
```

--- 
list combining

```py
>>> l = [1,2,3]
>>> l2 = [4,5,6]
>>> l + l2
[1, 2, 3, 4, 5, 6]
>>> l += l2
>>> l
[1, 2, 3, 4, 5, 6]
```