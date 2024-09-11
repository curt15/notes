Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python standard library]] [[builtins]]
Ref: 
Tags: #public 

--- 
#### locals(), 
locals() -> a *dict* of local variables

```py
>>> locals()
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>}
```

see also: [[globals]]

--- 

```py
# test.py
      

def see_local_vars(v1, v2):
        z = 'blah blah'
        loc = locals()
        print(f'locals: {loc}')


see_local_vars('x', 'y')
```
```py
$ python test.py

locals: {'v1': 'x', 'v2': 'y', 'z': 'blah blah'}
```

**LEGB rule**: local -> enclosing -> global -> built-in when resolving namespace

```py
>>> def print(var): return 'blah blah blah'
...
>>> print('hello world')
'blah blah blah'
```