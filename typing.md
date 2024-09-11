Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: 
Tags: #public 

--- 

```py
import typing
```

--- 
Optional
```py
 from typing import Optional
 
running_max : int = None

^^ this will get upset

running_max : Optional[int] = None

^^ allow to be an integer or None



```

Iterable
```py
from typing import Iterable
from collections import namedtuple

Item = namedtuple('Item', 'name, value')

def counter(items: Iterable[item] -> int):
	pass
	
^^^ will give editor hints and validate what going in and returning

vs "items... okay so it's probably multiple things and iterable"
```