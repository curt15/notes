Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[httpx]]

--- 

```py
import asyncio
```

--- 

concurrency = handling, but not doing in parallel.
you have to stop and switch tasks.


```py
#sentdex
import asyncio

async def find_divisibles(inrange, div_by):
    print("finding nums in range {} divisible by {}".format(inrange, div_by))
    located = []
    for i in range(inrange):
        if i % div_by == 0:
            located.append(i)
        if i % 50000 == 0:
        	await asyncio.sleep(0.0001) # suspends task at intervals (weird example, but just for quick show)
    print("Done w/ nums in range {} divisible by {}".format(inrange, div_by))
    return located

async def main():
	divs1 = loop.create_task(find_divisibles(508000, 34113))
	divs2 = loop.create_task(find_divisibles(100052, 3210)) # will sleep twice
	divs3 = loop.create_task(find_divisibles(500, 3)) # will never sleep
	await asyncio.wait([divs1,divs2,divs3])
	return divs1, divs1, divs3

if __name__ == '__main__':
	try:
		loop = asyncio.get_event_loop()
		#loop.set_debug(1)
		d1, d2, d3 = loop.run_until_complete(main())
		print(d1.result())
	except Exception as e:
		print('Shit fucked up yo')
	finally:
		loop.close()
```


--- 

[[ python ]]