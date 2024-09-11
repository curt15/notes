Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]
Ref: 
Tags: #public 

--- 
#### next()
moves **\_\_next\_\_** manually if **\_\_iter\_\_** is defined;
is effectively a step in a for loop
- generator expression: (i for i in range(100))

--- 

range as a class:
```py
class RangeExamp:
	def __init__(self, end, step=1):
		self.currt = 0
		self.end = end
		self.step = step

	def __iter__(self):
		return self

	def __next__(self):
		if self.curr >= self.end:
			raise StopIteration()
		else:
			return_val = self.current
			self.curr += self.step
			return return_val
```

range as a function:
```py
def range_func(end):
	curr = 0
	while curr < end:
		yield curr
		curr += 1
```