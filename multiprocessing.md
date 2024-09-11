Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: 
Tags: #public 

--- 

```py
import multiprocessing
```

--- 

Allows override of python Global Interpreter Lock (GIL)

see CPU usage changes in Activity Mangager

multiprocessing.Process(target, args)
```
def spawn(num,num2):
	print('Spawned! {} {}'.format(num,num2))

if __name__ == '__main__':
	for i in range(500):
		p = multiprocessing.Process(target=spawn, args=(i,i+1))
		p.start()
```