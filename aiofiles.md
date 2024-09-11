Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[asyncio]]; [[fastapi]]
Ref: [docs](https://pypi.org/project/aiofiles/)
Tags : #public 

--- 

 ```pip install aiofiles```
--- 

```py
import json
import asyncio

import aiofiles

async with aiofiles.open('settings.json', 'r') as f:
	cont = await f.read()
	cont = json.loads(cont)
	# -> 
	
```

--- 
make sure you ```async def```, otherwise get weird error ```AttributeError: __enter__```; interestingly a result (apparently) of the interpreter thinking you're attempting to re-assign the [[builtins]] open() function. https://stackoverflow.com/questions/53564755/python-error-attributeerror-enter
