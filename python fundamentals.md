Links: [[ PYTHON ]] - [[PROGRAMMING]]

--- 
contents: 
- [[#statements]]
- [[#conditions and control flow]]
- [[#more operators]]
- [[#more looping]]

--- 
#### statements

any individual line of code itself is commonly called a **statement**, such as each time we're *setting a variable* here: 
```py
>>> x = 'some text'
>>> y = 12
>>> z = 3.4
```

--- 
#### conditions and control flow

a *conditional* statement can be created by using the **keyword**s ```if``` or ```while```, and extended by ```and``` and/or ```or```. A ```bool``` ```True``` value to the overall statement allows the following **indented** code statement(s) to run.

```if```
```py
>>> x = 'some text'
>>> if type(x) == str:
...		print('this will print.')
...
this will print.
```

```py
if False:
    break
```


```while```
```py
>>> l = [1,2,3,4,5,6,7,8,9,10]
>>> while l:
...     print("curr list status: ", l)
...     l.pop()
... 
curr list status:  [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
10
curr list status:  [1, 2, 3, 4, 5, 6, 7, 8, 9]
9
curr list status:  [1, 2, 3, 4, 5, 6, 7, 8]
8
curr list status:  [1, 2, 3, 4, 5, 6, 7]
7
curr list status:  [1, 2, 3, 4, 5, 6]
6
curr list status:  [1, 2, 3, 4, 5]
5
curr list status:  [1, 2, 3, 4]
4
curr list status:  [1, 2, 3]
3
curr list status:  [1, 2]
2
curr list status:  [1]
1
>>> print(l)
[]

```

```and``` and ```or```
```py
>>> x = 'some text'
>>> y = 2 
>>> if isinstance(x, str) and y == 2:
... 	print('this will print.')
...
this will print.
>>> if isinstance(x, str) or y == 9000:
... 	print('this will print.')
...
this will print.
```

--- 
```pass``` 

allows for a conditional statement to do nothing without breaking. 

```py
>>> x = 'some text'
>>> if x:
... 	pass
... 
>>> # nothing happened
>>> # but, we didn't get an 
>>> # IndentationError
>>> if x:
... 
  File "<stdin>", line 2
    
    ^
IndentationError: expected an indented block
```

--- 

```is```

Where the ```==``` operator returns ```True``` for an equivalent object, the **keyword** ```is``` (by itself) only returns ```True``` for *the same* object.

```py
>>> x = 'some text'
>>> y = 'some text' 
>>> z = x
>>> x == y
True
>>> x is y
False
>>> x is z
True
>>> z is x
True
>>> id(x)
140537665644592
>>> id(z)
140537665644592
>>> x = 'some NEW text'
>>> z
'some text'
>>> x is z
False
>>> z = 'some NEW text'
>>> x is z
False
```

--- 

```elif```

a *conditional* statement can be extended to handle for additional potential (specific) conditions via ```elif```, 

```py
>>> x = 'some text'
>>> if isinstance(x, int):
... 	print('x is an integer.')
... elif isinstance(x, float):
... 	print('x is an float.')
... elif isinstance(x, str):
... 	print('x is a string.')
... 
x is a string.
```

```else```
a *conditional* statement can be extended to handle for **anything else not specified** via it's initial ```if``` or any of it's child ```elif```:


```py
>>> class MyThing:
... 	pass
>>> 
>>> x = MyThing()
>>> if isinstance(x, int):
... 	print('x is an integer.')
... elif isinstance(x, float):
... 	print('x is a float.')
... elif isinstance(x, str):
... 	print('x is a string.')
... else:
		print('x is something other than int, float, or string...')
x is something other than int, float, or string...
```

--- 

#### more operators

```=```, ```==```, ...

```+``` addition
```-``` subtraction 
```*```multiplication 
```**```exponentiation 
```/``` division 
```%``` modulus (remainder division)

```py
>>> 2 + 2 
4
>>> 4 - 2
2
>>> 2 * 4
8
>>> 4 ** 2
16
>>> 4 / 2
2.0
>>> # ^^ int division
>>> # results in float
>>> 4 % 2
0
>>> 4 % 3
1
>>> # ...
>>> # order of operations: 
>>> ((2 - 2) * 4) - 2 
-2
>>> ((2 - 2) / 4) - 2
-2.0
>>> 4 * ((2 + 2) + (4 / 2))
24.0
>>> 4 * ((2 + 2) + 4 / 2)
24.0
>>> 4 * (2 + 2) + 4 / 2
18.0
>>> 4 * (2 + 2 + 4 / 2)
24.0
```

--- 

#### more looping

**Looping** is walking through an iterable. We did this above with ```l = [1,2,3,4,5,6,7,8,9,10]``` and our conditional statement  ```while l:``` (so called, a "while loop"). 

```for``` and ```in``` are **keywords** that can be used together to loop through iterables (such as the builtin **containers** ```list``` and ```dict```):

```py
>>> l = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
>>> for x in l:
...     print(x)
... 
1
2
3
4
5
6
7
8
9
10
```
```py
>>> d = {'a':1, 'b':2, 'c':3, 'd':4}
>>> for k,v in d.items():
...     print('the key:', k, 'the val:', v)
... 
the key: a the val: 1
the key: b the val: 2
the key: c the val: 3
the key: d the val: 4
>>> # ... 
>>> for k in d.keys():
...     print('the key only:', k)
... 
the key only: a
the key only: b
the key only: c
the key only: d
>>> # ... 
>>> for v in d.values():
...     print('the val only:', v)
... 
the val only: 1
the val only: 2
the val only: 3
the val only: 4
```

--- 

### more data structures
```str```, ```int```, ```float```, 
```list```, ```dict```, 
...

```set```

```py
>>> l = [1,2,2,2,2,3,2]
>>> set(l)
{1, 2, 3}
```

```tuple```

```py
>>> l = [1,2,2,2,2,3,2]
>>> tuple(l)
(1, 2, 2, 2, 2, 3, 2)
>>> l = tuple(l)
>>> l.pop()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'tuple' object has no attribute 'pop'
>>> # one does not simply
>>> # change an immutable data type
```


--- 

### function basics 

a **function** is a collection of **statements**, initialized by the keyword ```def```, commonly serving a specific (single) purpose, defined as such for re-usability and generalization.



