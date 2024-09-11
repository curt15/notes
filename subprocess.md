Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: [docs](https://docs.python.org/3/library/subprocess.html);
Tags: #public 

--- 
```py
import subprocess
```

--- 

opposite of sys.argv (args from shell --> script as *list*)
spawns processes from script --> shell calls 

**subprocess.check_output()**
- shell=True - outputs the normal shell output -> terminal (cannot be stored as such)

```
def list_of_ls():
	"""
	:returns list: of current os.getcwd
	"""
	return subprocess.check_output('ls -d */', shell=True).decode('utf-8').splitlines()
```


**subprocess.run()**
- capture_output=True -> ability to string parse stdout & error (after converting byte to *str*)
```py
import subprocess

USERS = '/Users/'


def get_curr_user():
	return subprocess.run(['whoami'], capture_output=True).stdout.decode('utf-8').strip()
```
**subprocess.call()**[docs](https://docs.python.org/3/library/subprocess.html#older-high-level-api) - tl;dr use run^^