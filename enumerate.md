Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]

--- 
#### enumerate()
```py
exli = ['this', 'that', 'foo', 'bar']

for i in range(len(exli)):
	print(i, exli[i])

# ==>
for i, j in enumerate(exli):
	print(i, j)

exDic = {i:j for i, j in enumerate(exli)}
# {0: 'this', 1: 'that', 2: 'foo', 3: 'bar'}
```