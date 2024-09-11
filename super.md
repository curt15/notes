Links: [[PYTHON]] - [[PROGRAMMING]]
Ref: [[python standard library]]; [[builtins]]

--- 
super() - best used to access parent methods when overwriting, but still want access, specifically handy as without having to name the MRO parent of which accessing. 

```py
>>> class MyBaseThing:
...     def hello_(self, name):
...             return f'hello {name}'
... 
>>> class MyThing(MyBaseThing):
...     pass
... 
>>> x = MyThing()
>>> x.hello_('world!')
'hello world!'
>>> class MyThing(MyBaseThing):
...     def __init__(self):
...             pass
... 
>>> x = MyThing()
>>> x.hello_('world!!')
'hello world!!'
>>> 
>>> # still accessable w/out calling super(), ... when to use super() then?
>>> 
>>> class MyThing(MyBaseThing):
...     def hello_(self, name):
...             x = super().hello_(name)
...             x += '!!!!!!!!!!'
...             return x
... 
>>> y = MyThing()
>>> y.hello_('world')
'hello world!!!!!!!!!!'
>>> 
>>> class MyThing(MyBaseThing):
...		pass
>>> 
>>> class MyNextInLineThing(MyThing):
...     def __init__(self, myname: str):
...             self.myname = myname
...     def hello_(self):
...             name = input('"Stranger, what\'s your name?"\n: ')
...             resp = super().hello_(name) + f',\nMy name is {self.myname}.'
...             return resp 
... 
>>> x = MyNextInLineThing('Gerald')
>>> x.hello_()
"Stranger, what's your name?"
: Mary Lou
'hello Mary Lou,\nMy name is Gerald'
```