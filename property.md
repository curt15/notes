Links: [[INDEX]] - [[PYTHON ]]

[[python decorators]] - @property is a decorator

properties = things that extend dynamically

--- 

@property can be used to create a dynamic instance variable, allowing you to have attributes that update when the source attributes are modified:

```py

class Person:
	def __init__(self, fn, ln):
		self.fn = fn
		self.ln = ln
	
	@property
	def full_name(self):
		return f'{self.fn} {self.ln}'


>>> p = Person('Curt', 'Brun')
>>> p.full_name
'Curt Brun'
```
and a setter can be defined to allow modifications of the fn and ln by simply assigning a new full_name str:
```py
	#...
	@full_name.setter
	def full_name(self, name):
		self.fn, self.ln = name.split()

>>> p.full_name = 'Joe Brun'
>>> p.fn
'Joe'
>>> p.ln
'Brun'
	
```

-> deleter
```py
	#...
	@full_name.deleter
	def full_name(self):
		self.fn, self.ln = (None, None)

>>> (p.fn and p.ln) == None
True
```



--- 
-> https://www.programiz.com/python-programming/property as alt to getters and setters

References:
- https://www.machinelearningplus.com/python/python-property/
