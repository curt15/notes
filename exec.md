Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]
Ref: 
Tags: #public 

--- 

#### exec()
compiles and evaluates a statement or set of statements you passed through in string form
"Dangerous on virtual machine" (?)
```py
exec("print('so this works like eval.')")

>>> exec('x = 2') # adds x to the global namespace
>>> exec('if x == 2: print("x is two")')
x is two
```


--- 

References:
- https://stackoverflow.com/questions/2220699/whats-the-difference-between-eval-exec-and-compile
- 