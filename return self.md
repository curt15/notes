Links: [[PYTHON]]
Rel: 
Ref: [return self](https://stackoverflow.com/questions/43380042/purpose-of-return-self-python)
Tags: #public 

--- 

```py
>>> class Counter(object):
...     def __init__(self, start=1):
...         self.val = start
...     def increment(self):
...         self.val += 1
...         return self
...     def decrement(self):
...         self.val -= 1
...         return self
...
>>> c = Counter()
```
-> now, chain-able method calls
```py
>>> c.increment().increment().decrement()
<__main__.Counter object at 0x1020c1390>
```
