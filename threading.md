Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]

--- 
```py
import threading
```
--- 

Threading allows you to do simultaneous tasks run concurrently (parallel).

Basic:
```
def sleeper(n, name):
	print('Hi I am {}. I am going to sleep for {} seconds\n'.format(name, n))
	time.sleep(n)
	print('{} has woken up from sleep\n'.format(name))


t = threading.Thread(target=sleeper, name='thread1', args=(5, 'thread1'))
t.start()
# t.join() # this prevents the script to contiune until the  task is completed

# Without t.join(), despite t not finishing the sleeper task, the rest of the program can run.
print('hello')
print('hello')
```

--- 

[[ python ]]