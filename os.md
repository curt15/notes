Links: [[PYTHON]] - [[PROGRAMMING]]
Ref: [[python standard library]]

--- 

```py
import os
```

--- 




**os.getcwd()**

os.chdir(path)

**os.mkdir()**
```os.mkdir('new_folder_in_current_path')```

**os.rename()**
```os.rename('this_folder', 'that_folder')```

**os.rmdir()**
```os.rmdir('this_folder')```

#### os.path.join()
```
import os

my_documents = '/Users/cbrun3/Documents/'
ex_file = 'example.txt'

print(location_of_file + '/' + ex_file) # the full path

with open(os.path.join(my_documents, ex_file)) as f:
	print(f.read())
```

**os.listdir(path='.')**

os.remove(path, \*,)

---
```py
os.path.dirname(__file__)
os.path.abspath(__file__)
```
--- 

[[ python ]]