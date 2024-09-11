Links: [[PYTHON]]
Rel: 
Ref: https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes <-- go here
Tags: #public 

--- 

basic timing!?
```py
import datetime

t0 = datetime.datetime.now()
# some function running -> 
t1 = datetime.datetime.now()
dt = t0 - t1
print(f'Finished running in {dt} seconds.')
```

file mod datetime:
```py
import datetime
import os

d = datetime.datetime.fromtimestamp(os.path.getmtime('.gitignore'))

d.year
d.month
# ...

```

datetime.datetime.strftime()
```py
>>> print(datetime.datetime.strftime(datetime.datetime.now(), '%X %p'))
11:17:27 AM
```