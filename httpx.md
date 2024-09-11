Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python 3rd party packages]]
Ref: [docs](https://www.python-httpx.org/)

like [[requests]], but supports async

--- 
```pip install httpx```

--- 

```py
import httpx
```

--- 


```py 
import httpx

async def get_html(url):
	async with httpx.AsyncClient() as client:
		resp = await client.get(url)
		resp.wait_for_statuses()
		return resp.text
```

