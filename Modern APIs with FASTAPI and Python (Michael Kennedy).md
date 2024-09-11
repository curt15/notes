Links: [[PROGRAMMING]] - [[PYTHON]]
Ref: [course link](https://training.talkpython.fm/courses/details/getting-started-with-fastapi?require_login=true), https://openweathermap.org/api,  https://www.uvicorn.org, 
Tags: #course --> [[rlparse]] ?
Rel: [[fastapi]], [[typing]], [[httpx]], 

https://talkpython.fm/linode for $100 credit!

He uses [[homebrew]] and [[chocolatey]] to install python. Uses pycharm, reccomends also  

Don't put your secrets on git: https://www.shhgit.com/.

server:  https://www.uvicorn.org/  "fastapi built on starlette, uvicorn built on Starlette and made by Starlette, so may as well use this" 
etc asgi: https://github.com/florimondmanca/awesome-asgi

Jinja2 - templating language built in (thinks Chameleon is vastly better than this or Django template language) ```pip install jinja2```
aiofiles - necessary to serve static files in fastapi (is an async http file transfer lib) ```pip install aiofiles```

SQLAlchemy supports async await, and things that work with mongoDB, redis, and even files, etc. just need to find libraries that support. 



--- 

Why FastAPI?

- Fast to execute: Very high performance, on par with NodeJS and Go (thanks to Starlette and Pydantic). One of the fastest Python frameworks available.
- Fast to code: Increase the speed to develop features by about 2x - 3x faster
- Fewer bugs: Reduce about 40% of human (developer) induced errors.
- Intuitive: Great editor support. Completion everwhere. Less time debugging.
- Easy: Designed to be easy to use and learn. Less time reading docs.
- Short: Minimize code duplication. Multiple features from each parameter declaration. Fewer bugs.
- Robust: Get production-ready code. With automatic interactive documentation.
- Standards-based: Based on (and fully compatible with) the open standards for APIs: OpenAPI (previously known as Swagger) and JSON
- Type hints, async / await, ASGI servers, Data classes, Pydantic classes, OpenAPI documentation, pytest, rich editor support.

FastAPI vs django, Flask - is an API framework with it's main goal as APIs, don't support async currently


 BIG IDEAS:
 - First API
 - Language features
 - Pydantic - model data exchange and validation
 - Serving HTML
- A full featured API
- Deployment


HTTP VERBS:
| Verb | Meaning |
| :--: | :--: |
| GET | requests a representation of the specified resource. Requests using GET should only retrieve data. (read-only). |
| POST |  submit an entity to the specific resource, often causing a change in state or side effects on the server. |
| DELETE |  remove a resource. |
| PUT | replaces all current representations of the target resource with the request payload. |



https://httpstatuses.com/

--- 

WSGI - older, non-asynchronous 
Web Service Gateway Interface
- expects you pass functions, request is called, process, return value is returned, 
- 
```py
def request(environ, start_response):
	r = start_response(environ)
	# ...
	return r
```

ASGI
Asyncronous Server Gateway Interface
```py
async def app(scope, recieve, send):
	r = await recieve(scope)
	# ...
	return await send(r, scope)
```
allow many requests at the same time



```py
@router.get('/api/weather/{city}')
def weather(city: str, 
			state: Optional[str] = None,
			country:str = 'US',
			units: Optional[str] = 'metric'):   

	return f"Some Report for {city}, {state}, {country}, in {units}"
```
->
```py

```

Instead of "get bad data" -> "crash" (Internal Service Error)
convert exceptions and errors on the server to fastapi.Response 's to communicate the error

Error handling makes services much more durable



Data access layer ~= internal service;
created Report model, data access layer, now easy to build API around


If you're putting into production and you don't want it to be a public API, take away the /docs url by:
```py
api = fastapi.FastAPI(docs_url=None)

```

--- 

nginx front-end web server; web request comes in, SSL exchange, etc. -> 
gunincorn manage lifecycle, many copies of application running in ->  
uvicorn asyncronous loop version (each process, new requests get fanned out between processes to not overwhelm any one of them). 

create server via site gui
log in, upgrade & update apt
non-root user 
configure firewall, etc.
git code in
venv
pip install requirements


httpie

default venv via zshrc

--- 


import fastapi
import uvicorn

api = fastapi.FastAPI()

@api.get('/api/myendpoint')
def myendpoint():
return 'something'



running_max: Optional[int] = None

Optional[int] means it can be an integer or None

def counter(items: Iterable[Item]) -> int:
total = 0
...
return total



type hints -> conversions and validations (via Pydantic types (e.g. BaseModel))


async view methods 
when waiting on external services, let other stuff run 


Rendering TEMPLATES

Status codes and responses 

letsencrypt

--- 
### Ch 8. Deploying FastAPI on Linux with gunicorn and nginx

Heroku (a PaaS)
Linode -> kubernetes -> docker 
AWS (simple = Amazon Lightsail), Azure 

Ubuntu VM 

GUI->
- pick data center that makes sense
- Authentication -> SSH key (no user/pass to mess with)
- name it
- run
- copy IP address
- DONE.

ssh ->
```sh
ssh root@ipaddress
# yes, exchange keys
```
```sh
apt update && apt upgrade
``` 
log out -> log in ->
```sh
apt list --upgradable
```
when you see "Linux Headers", means a new kernel upgrade too. Apply ->
log out -> log in ->
see if "\*\* System restart required \*\*" ->
```sh
reboot
```
DONE.
-> 


Overall architecture / topology:
- Ubuntu VM : everything running in
	- NGINX : first thing someone coming to server interacting with; servers HTML, CSS, does SSL, etc. (not where the python code runs)
	- gunicorn : (uvicorn is the asynchronous loop version of Gunicorn used to run FastAPI) is more proper server; manages life cycle of apps runnning (e.g. one of apps gets stuck in process and freezes up, Gunicorn has a way to run in supervisor mode and tell you "thing stuck / ran out of memory, lets restart it so the server doesn't perm go down, just small glitch for a user, and then move on"). 
	- uvicorn (times X) : is where python code runs and lives (in many parallel instances) -> 
- https -> NGINX (SSL exchange, etc. -> "oh this request going to fast api application") -> request (via http or Linux sockets directly) -> gunicorn ("okay, got this request to this application, and there's prob a bunch going in parallel, which one of these worker processes are not busy and can handle a request? this one. and for this new request? that one. etc.") -> fans out requests to uvicorn to not overwhelm a single one. 
- -> 




**src/server/nginx/weather.nginx**- config file
src/server/server_setup.sh 
- get git, python, etc. (zsh...)
- # git already standard ... 
- # zsh for pretty terminal -> unnecessary 
- sudo apt-get install -y -q python3-pip python3-dev python3-venv
- python3 -v 
- sudo apt install fail2ban -y (try to log in to server too many times, get banned! brute force / dictionary attacks)
- ufw allow 22  (firewall...)
- ufw allow 80
- ufw allow 443
- ufw enable
- apt install acl -y (don't want to be root...)
- useradd -M apiuser
- usermod -L apiuser 
- setfacl -m u:apiuser:rwx /apps/logs/weather_api
- ...
- mkdir apps/
- chmod 777 apps/
- mkdir apps/logs
- mkdir apps/logs/weather_api/app_log
- cd /apps
- ...
- python -m venv venv
- ...
- git clone https://github.com/pysidian/blog app_repo
- cd app_repo/
- pip install -r requirements.txt
- set-up the .env / settings.json
- python3 main.py
- curl http://127.0.0.1:8000 (to test)
- -> don't want to run as main.py, want system to run (ctrl+C or log-out -> service stops!). Want to create a SystemD service or daemon so that on server start-up, our python webapp is running automatically. 
- need venv activated on log-in ->
- nano .zshrc 
- -> source /apps/venv/bin/activate
- log out -> log in -> pip list 
- ...
**src/server/units/weather.service**
- test the ExecStart command 
- pip install wheel # setuptools <- standard 3.8
- *pip install --upgrade gunicorn uvloop httptools*
- try without logging and get messages to terminal 
- -> copy and start the daemon:
- cp /apps/app_repo/server/units/weather.service /etc/systemd/system/
- systemctl start weather
- systemctl status weather
- systemctl enable weather
- -> reboot -> on restart, should be running service again
- http localhost:8000
- -> set up nginx (frontend web server) so can talk to web
- **apt install nginx**
src/server/nginx/weather.nginx
- server_name -> ipaddress
- rm /etc/nginx/sites-enabled/default
- cp /apps/app_repo/server/nginx/weather.nginx /etc/nginx/sites-enabled/
- update-rc.d nginx enable
- service nginx restart 
- http localhost:8000
- http localhost (talk to nginx)
- -> browser check @ ip address 
- ... 
- -> inspect -> Network -> how quick is request? (35ms?)
- -> adding SSL: buying? so two years ago. (use letsencrypt... beautiful, free, automatic way to keep SSL certificate)
- add-apt-repository ppa:certbot/certbot
- apt install python-certbot-nginx
- certbot --nginx -d weatherapi.talkpython.com
	- point DNS to server first ->
	- email: ...
	- -> accept yes / no's (say yes to redirect if someone hits non-SSL)


--- 
Conclusion:
production-grade APIs with FastAPI

```py
import fastapi
import uvicorn

api = fastapi.FastAPI()

@api.get('/api/calculate')
def calculate():
	return 2 + 2

uvicorn.run(api, host='127.0.0.1', port=8000)
```

Type hints applied (somewhat like static languages, being picky)
```py
running_max: Optional[int] = None

def counter(items: Iterable[Item]) -> int:
	total = 0
	
	# ...
	
	return total
```
^^ with Pydantic + FastAPI, doing more than documenting type information, actually doing things like type conversions and checking for required (Optional, non-, etc.) values. 

Pydantic types:
```py
from pydantic import BaseModel
from typing import List, Optional

class Order(BaseModel):
	item_id: int
	created_date: datetime.datetime
	price: float
	pages_visited: Optional[List[int]] = []	
```
^^ describe data concisely ->
```py
order_json = {
	'item_id': '123',
	'created_date': '2002-11-24 12:22',
	'pages_visited': [1, 2, '3'],
	'price': 17.22
}

order = Order(**order_json)
```
^^ where not exactly what were looking for, but convertable (e.g. item_id='123' (str) -> item_id=123 (int))

async view methods:
```py
import fastapi
router = fastapi.APIRouter()

@router.get('/api/weather')
async def weather(city: str, country: Optional[str] = 'US', state: OPtional[str] = None, units: str = 'metric'):
	report = await openweather_service.get_report_async(city, country, state, units)
	return report
```
^^ taking the times where we're waiting (e.g. on external services) and allow other code to run (database to get back to us, external API calls, ping times, ...) -> fastapi natively supports async 

Rendering TEMPLATES:
```py
templates = Jinja2Templates(directory="templates")

@router.get('/')
def home(request: Request):
	return templates.TemplateResponse('index.html', {'request': request})
```
^^ is api first, so treats as JSON out of box -> basic web stuff w/ jinja templating. ```pip install jinja2```.

Status codes and responses :
```py
@router.get('/api/weather/{city}')
async def weather(loc: Location = Depends()):
	try:
		return await openweather_service.get_report_async(loc.city, loc.country, loc.state, loc.units)
	except ValidationError as ve:
		return fastapi.Response(content=ve.error_msg, status_code=ve.status_code)
	except Exception as x:
		print(f'Server crashed while processing request: {x}')
		return fastapi.Response(content="Error processing your request.", status_code=500)		
```
https://httpstatuses.com to see what meaningful status code you should be using when handling.

Modifying data through the API:
```py
from pydantic import BaseModel

class Location(BaseModel):
	city: str
	country: Optional[str]
	state: Optional[str] = None
```
```py
class ReportSubmittal(BaseModel):
	location: Location
	description: str
```
```py
@router.post('/api/reports', name='reports')
async def reports_post(report: ReportSubmittal):
	return await report_service.add_report(report.description, report.location)
```
^^ post success should be 201 (vs 200 OK GET). This is automatic.

Overall architecture / topology:
--> get it online so it can be consumed by other applications
nginx -> gunicorn -> uvicorn, uvicorn, uvicorn, ... <-- 
