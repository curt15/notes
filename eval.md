Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]
Ref: 
Tags: #public 

--- 
#### eval()
why can it be dangerous?
evaluates an *single expression* (anything you can put as value of a variable assignment as *str*) and returns the value that the expression produces.
- can't assign variables ('x = 2') or run statements ('if x == 2: print("x is two")')
```py
list_str = "[2,9,4,3,17,20]"
evald_str = eval(list_str)

>>> type(evald_str == list)
True
```
alineof.py
```py
def hack_the_thing():
	x = input("code: ")
	evald_x = eval(x)
	return evald_x

if __name__ == '__main__':
	hack_the_thing()

```

see also: [[exec]]