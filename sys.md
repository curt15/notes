Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]

--- 
```py
import sys
```

--- 

sys **.argv**
a **list** of arguments with the name of called module at index 0
``` # example.py
if len(sys.argv) > 1:
	print(sys.argv[1])

$
$
$python3 example.py 'This is a thing'
This is a thing
```

--- 

color error output?
```
sys.stderr.write('This is stderr text\n') #should be red?
sys.stderr.flush()
sys.stdout.write('This is stdout text\n')
```


sys.exec_info [ docs ](https://docs.python.org/3/library/sys.html#sys.exc_info)
"executing an except clause"
(type, value, traceback)
```
def error_handling():
	return ' {}. {}, line: {}'.format(
		sys.exc_info()[0],
		sys.exc_info()[1],
		sys.exc_info()[2].tb_lineno)

try:
	a+b
except Exception as e:
	logging.error(error_handling())
	print(sys.exc_info()) # tuple    

...
>>>
ERROR:root: <class 'NameError'>. name 'a' is not defined, line: 2

(<class 'NameError'>, NameError("name 'a' is not defined"), <traceback object at 0x109230d20>)
```


--- 

[[ python ]]