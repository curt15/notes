Links: [[PROGRAMMING]]
Tags: #media 

--- 
[postgreSQL when not your job](https://www.youtube.com/watch?v=fva7qn9Yg3o )

https://www.saltstack.com/

https://www.djangoproject.com/

https://12factor.net/

https://en.wikipedia.org/wiki/CPanel
https://en.wikipedia.org/wiki/Salt_(software)


--- 


**heroku vs webfaction**
https://www.reddit.com/r/django/comments/9fll2g/how_do_you_update_your_deployed_webapp/

heroku = PAAS
linode/EC2 = VPS
webfaction = mix
- "1 click installer" for Django
- access to shell, chrontab
- can write scripts, machine-machine interaction
- sys-admins handle much of "boring and repetitive" (but hard) e.g. package management, installation, and security

______

Docker:

"TeamCity" auto builds the new Docker image whenever commit. commit to master -> puch new image to DockerHub -> SSH into server and run script to stop current container, update image, start new container w/ migrations, starts Celery daemons.



KISS method:

1 - git pull

2 - python manage.py migrate (if need)\

3 - python manage.py collectstatic (if need)

4 - restart Apache (yes I use mod_wsgi)

- Docker, etc. makes sense for multi-server deployment or want to deploy EVERYTHING every time. 

- "In my case" running production on a single, low traffic server, with lots of legacy shit still in the middle of replacing piece by peace



Fabric:

- write it in python code

- it provides diff kinds of tasks etc that can run on another comp over SSH connection

- if not needed Jenkins/Travis CI/AWS Code deploy this is next best ("IMO").



Dokku:

- free, easy to use/set-up own server

- open source

- docker

- https://12factor.net/

- handles backing services (db, cache, etc.)



Classy Django REST Framework:

http://www.cdrf.co/

http://ccbv.co.uk/projects/Django/2.2/







____________

https://www.gandi.net/en/domain

https://njal.la/

https://www.orangewebsite.com/







LUKS

_____________________________________________________________

SITE / HOSTING INFO



So I'm going to offer advice you're not going to like, but I highly suggest the process having recently gone through a similar learning process as you seem to be in now.



Get a blank VPS

https://www.slant.co/topics/3444/~best-cloud-hosting-services-for-small-businesses#4

https://www.linode.com/

https://www.a2hosting.com/django-hosting?aid=318dd9f8&data1=f1cinxsxbfqcpgsj__2

https://ramnode.com/





Getting your own server, installing the necessary packages, and getting things up and running is incredibly empowering, and will also teach you a ton about where bottlenecks lie in your application, things you'll need to consider to scale, etc.



In terms of pricing - look around a bit, but there are some dirt cheap VPS vendors out there with solid track records. I happen to really like RamNode (one of the only providers out there that offers SSDs, and at dirt cheap prices too), another I've heard good things about is BuyVM, or Prometheus if you're in the EU. Many of these vendors start their offerings at $24/year, and you can get excellent hardware at very decent prices.



So get yourself a server, and then:



Learn a configuration management suite



I'll recommend SaltStack -- I previously used Chef, and salt is much easier IMO to both learn and use. You'll spend a day or two wrapping your head around how to use it/set it up/etc, but this will be well worth your time once you do.



This will let you set up your server once, and once it's all set up, automate rebuilding it over and over again if you need to. It will give you a great deal of peace of mind, and will make ongoing maintenance and updates a dream.



Finally:



Figure out how to set up your stack



Here's where things get sexy. Building a stack for your app will teach you SO much. Here are my recommendations to get you started:



    DB: Postgresql (And google the talk "Postgresql when it's not your job" -- really good configuration advice)



    Cache: Redis (Use the django-redis-cache backend -- redis is nice because it's as fast as memcached, but is fairly persistent, so you can keep your sessions as 'cache' instead of 'cached_db', and on reboots, won't end up logging out all your users)



    Front-end Web Server: nginx (This is an incredible server, can do front-end caching, load balancing, and works really nicely with the wsgi server I'm recommending next)



    WSGI server: uwsgi (Very solid, and has a number of extremely useful configuration options - also, nginx "speaks" uwsgi protocol) Alternative: gunicorn (a bit easier to get started with, but missing very nice extra features)



And that's it.



Now I won't kid you -- this is probably going to be a 2-3 month process and a lot of learning. But you'll be much better off for it, from writing better django apps because you understand the architecture they run within, to not being bound by hosting providers that upsell ease-of-use.



Or, just use Heroku



It's a popular choice, expanding into enterprise markets, and will be useful experience for deployment you may end up doing in future work. I still think this is really an option for once you've done the other process and want other people to manage it (but understand what elements you want them to manage, and why), but I also understand the draw of immediacy.



Hope this helps you, or someone else stumbling across this topic.

_____________________________________________________________

