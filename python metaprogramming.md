Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: 
Ref: 
Tags: #public 

--- 

Metaprogramming:
decorators 
metaclasses 
exec()

--- 

change_method_name()
```py
class A:
	def __init__(self):
		pass

	def func(self):
		print('func derived from A')

class B:
	def __init__(self):
		pass

	def func(self):
		print('func derived from B')

class C(B,A):
	def __init__(self):
		super().__init__()

c = C()
c.func()


def change_method_name(cls, name):
	def method(self):
		print('func from changed_func')

	method.__name__ = name
	return setattr(cls, name, method)


change_method_name(A, 'changed_func')


a = A()
a.changed_func()
```