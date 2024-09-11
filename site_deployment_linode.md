Links: [[PROGRAMMING]]
Rel: [[site_deployment]]
Tags: #media 
Ref: 
- https://pythonprogramming.net/deploying-to-server-django-tutorial/
- https://www.youtube.com/watch?v=4FLb1ulb64o

--- 

... 
- linode allows “stack script”
- “create new Linode”
- “select image”
  -“for now doing hard/our way by typing it in” (Older images -> Ubuntu 18.04 LTS)
  - LTS = “long term support”
- select “Region”
  - US Dallas, TX = “nice, central location”
- select “Linode Plan”
  - Nanode 1GB = $5/mo
- “Linode Label”
  - django-video-tutorial
- “Root Password”
- “Backups” []
  - $2/mo
  - “later can use scripts, but always choose and never regretted it”
- “Private IP” []
  - he skipped
—> “Create”

OR

- “Create from StackScript”
- choose/upload

--- 

can SSH via terminal, use their “Launch Console”, or…

PuTTY — give IP address after ssh.root@

- “security message!” - ok on first click, trusting it as new, but in future if seen “something is wrong” (e.g. malicious re-point of domain)
- login with credentials set


apt-get update
- always do this first

apt-get install -y python3-pip
- -y just says “yes”

(can update to python 3.7 “on own time”)

python3 -m pip install —upgrade pip

- ensure pip is up to date

pip install django

pip install django-tinymce4-lite

- etc. for each needed/used

mkdir /var/www

- leading with “/“ for root

cd /var/www

django-admin startproject mysite



nano mysite/mysite/settings.py

DEBUG => FALSE

ALLOWED_HOSTS => [‘Reverse DNS’] (e.g. li914-174.members.linode .com)

- “is for temporary domain name”

- make domain name, register it w/ registrar, on registrar point domain name to the host’s name servers (“linode name servers”), on linode - point domain name to specific linode, then that linode will point based on specific domain name (i.e. can have multiple sites hosted on a single server)



cd mysite/

python3 manage.py startapp it_works

nano it_works/urls.py

- copy paste

nano it_works/views.py

- copy paste



“now we have server in the cloud, django set up,

now need to set up webserver, and for django to talk to webserver need intermediary (wsgi = “web server gateway interface”)”



apt-get install -y apache2

apt-get install -y libapache2-mod-wsgi-py3



(“why not nginx? because we had to pick one. question, done”)

nano /etc/apache2/sites-available/mysite.conf

- copy paste “virtual host stuff”

  - “your webserver can server many websites, server runs webserver, goes to virtualhost file, and looks at “hostname” (ServerName) and if it matches it does things based on that match”

  - “hostname” = linode -> networking -> Reverse DNS



a2ensite mysite

- “To activate the new configuration, you need to run:”

systemctl reload apache2



visit the “Reverse DNS temp url”

- he got the apache default page



rm /etc/apache2/sites-available/000-default.conf

- remove default conf

nano /etc/apache2/sites-available/000-default.conf

- copy paste stuff (“ServerName _” so that doesn’t have preference on hostname)

systemctl reload apache2

visit the “Reverse DNS temp url”

- “It works! (served from Django)”



_______

deploying project you’ve been working on:



“prob worked locally and now you want to put on server, million ways to do this,”

SCP (mac/linux and powershell) (win stp = windows gui version, sftp = e.g. filezilla, …)



wget “part 11 django” (grabs content online)

rm -r mysite/

apt-get install unzip (“tar might work too, but pain in butt to use”)

unzip django-11.zip 



edit same settings.py from before



go through django docs “Deployment checklist”

- “cant conver all security things, e.g. we used root user, probably in practice you would make your own sudo-er and users and disable the root user account — also, prob not log-in w/ passwords, use an SSH key, 

- save SECRET_KEY in file somewhere outside of Django project files



service apache2 reload

check url in browser

- “static not loading, in production need to handle static differently…”

nano mysite/settings.py

- under “STATIC_URL” - he added STATIC_ROOT, MEDIA_URL, MEDIA_ROOT



python3 manage.py collectstatic

- “In production need all static files in one location vs in each app”



back to broswer -> “refresh” ==> “everything working!”



- issues with main/urls.py and - “I always like to add trailing slashes, if don’t have and someone adds, will fail, if have and don’t add, will redirect (usually/flask/etc)”

  - delete all e.g. “register/“ -> “register”



service apache2 reload

- now can login, register, etc.

- login ==> “Server Error (500)”

  - “luckily I know what problem is, can read from the database, but don’t even have permissions fully to do that”

  - give user attempting to read the db permission to do so

chown www-data mysite/ (“www-data” is the apache user (?))

chown www-data mysite/db.sqlite3

service apache2 reload



DONE.

“django rest stuff doesn’t fit this example - maybe for single page app or other ‘restful api type thing’“

















