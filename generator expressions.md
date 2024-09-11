
--- 
generators are
**faster than list comprehensions (at scale)?**
```
in_nums = range(100)

def is_divisible_by_five(n):
	"""
	:return bool:
	"""
	if n % 5 == 0:
		return True
	else:
		return False

xyz = (i for i in in_nums if is_divisible_by_five(i)) # generator expression
xyz = [i for i in in_nums if is_divisible_by_five(i)] # list comprehension
```

which is faster to iterate?
```
import timeit

print(timeit.timeit("""
in_nums = range(100)

def is_divisible_by_five(n):
	if n % 5 == 0:
		return True
	else:
		return False

xyz = (i for i in in_nums if is_divisible_by_five(i))
	"""))
# 0.807376595000278
```
generator -> 0.807376595000278s
```
print(timeit.timeit("""
input_list = range(100)
def is_divisible_by_five(n):
	if n % 5 == 0:
		return True
	else:
		return False

xyz = [i for i in in_nums if is_divisible_by_five(i)]
	"""))
# 17.095245823001278
```
list comprehension -> 17.095245823001278s

the generator in that consists of numbers if they are divisible by 5 in range(100)

vs. building the list into memory 

the generator calculates the expression when **next()** is called ? 



--- 

a generator function
```
def hello_world_gen():
	yield 'Hello'
	yield 'World'
	yield '!'

for e in hello_world_gen():
	print(e)

```



---

[[ python ]]