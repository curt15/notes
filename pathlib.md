Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: 
Tags: #public 

--- 

```py
import pathlib
from pathlib import Path
```

--- 
module relative path
```py
module_fp = Path(__file__).parent
settings = module_fp / 'settings.json'

with settings.open() as sf:
	print(sf.read())
```