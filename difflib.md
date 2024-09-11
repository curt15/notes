Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: https://docs.python.org/3/library/difflib.html

--- 
```py
import difflib
```

--- 
difflib.get_close_matches(word, possibilities, n=3, cutoff=0.6) [docs](https://docs.python.org/3/library/difflib.html#difflib.get_close_matches)
- ```n``` -  maximum number of close matches to return
- ```cutoff``` - a float in the range 0,1.  Possibilities that don’t score at least that similar to _word_ are ignored.

```py
>>> get_close_matches('appel', ['ape', 'apple', 'peach', 'puppy'])
['apple', 'ape']
>>> import keyword
>>> get_close_matches('wheel', keyword.kwlist)
['while']
>>> 
get_close_matches('pineapple', keyword.kwlist)
[]
>>> get_close_matches('accept', keyword.kwlist)
['except']
```
