Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]

--- 
```py
import json
```

--- 

write dict to JSON file:
```
import json

def to_json(d, f):
	with open(f, 'w') as write_file:
		json.dump(d, write_file, indent=4)
```

load JSON file to dict:
```
import json

def from_json(f):
	with open(f, 'r') as read_file:
		in_dict = json.load(f)
	return in_dict
```

pretty print dict to JSON:
```

```

--- 