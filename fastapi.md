Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[tortoise-orm]], [[jinja2]], [[aiofiles]], [[python-decouple]], [[python-multipart]],
Ref: [home](https://fastapi.tiangolo.com/); [tutorial](https://fastapi.tiangolo.com/tutorial/); [dependency Injection](https://fastapi.tiangolo.com/tutorial/dependencies/)
- https://stackoverflow.com/questions/67774905/make-depends-optional-in-fastapi-python <- didn't work
- https://github.com/encode/starlette/issues/538#issuecomment-780608541 <- solved url_for http -> https absolute static path issue.

--- 

```pip install fastapi```
```pip install uvicorn```

```pip install passlib``` + ```pip install bcrypt``` = hashing passwords
```pip install pyjwt```  https://jwt.io <- check the generated token contents 

--- 


 
```py
import fastapi
import uvicorn

api = fastapi.FastAPI()
```



```sh
$ sqlite3 db.sqlite3
sqlite> select * from user;
```
--- 

--- 
Depends, oauth2_scheme

```py
@router.get('/api/testdepends', dependencies=[Depends(oauth2_scheme)])
async def test_depends(x: str):
	""" """
	return {'test': f'success {x}'}
```

--- 
--- 

### DEPLOYMENT: 

```
apt update && apt upgrade
reboot
```

```
apt-get install -y python3-pip python3-dev python3-venv 
apt install fail2ban -y
apt install acl -y 
useradd -M curtis
useradd -L curtis # ??? 
```

```
mkdir /apps/
mkdir /apps/logs/
mkdir /app/logs/blog_api/
touch /app/logs/blog_api/access.log
touch /app/logs/blog_api/errors.log

git clone https://github.com/prettynb/pnbp-blog /apps/blog
# set-up the blog/ .env file ->

chmod -R 777 /apps/
setfacl -m u:curtis:rwx /apps

python3 -m venv /apps/venv

echo 'alias activate=". /apps/venv/bin/activate"' >> /root/.bashrc
echo 'activate' >> /root/.bashrc
reboot
which python3
which pip3

pip3 install wheel gunicorn uvloop httptools
pip3 install -r /apps/blog/requirements.txt
```
```
mkdir /root/notes
echo 'export NOTE_PATH="/root/notes"' >> /root/.bashrc
```

```
# git local/, initialize API user id=1
# ... 
```

```
ufw allow 22
ufw allow 80
ufw allow 443
ufw enable
```

```
apt install nginx

mkdir /apps/blog/server/
mkdir /apps/blog/server/units/

rm /etc/nginx/sites-enabled/default
cp /apps/blog/server/blog.nginx /etc/nginx/sites-enabled/

update-rc.d nginx enable
service nginx restart
```
```
cp /apps/blog/server/units/blog.service /etc/systemd/system/

systemctl start blog
systemctl status blog
systemctl enable blog
```

```
apt-get install --reinstall ca-certificates
update-ca-certificates

add-apt-repository ppa:certbot/certbot
apt install python-certbot-nginx
certbot --nginx -d mydomain.com
# ^^ first, redirect DNS...
```

--- 
myapp.nginx
```
server {
    listen 80;
    server_name str.wiki 165.232.151.84;
    server_tokens off;
    charset utf-8;

    location /static {
        gzip            on;
        gzip_buffers    8 256k;

        alias /apps/blog/static;
        expires 365d;
    }
    location / {
        try_files $uri @yourapplication;
    }
    location @yourapplication {
        gzip            on;
        gzip_buffers    8 256k;

        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Protocol $scheme;
		
		proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }
}
```
->
```
server {
    server_name str.wiki 165.232.151.84;
    server_tokens off;
    charset utf-8;

    location /static {
        gzip            on;
        gzip_buffers    8 256k;

        alias /apps/blog/static;
        expires 365d;
    }
    location / {
        try_files $uri @yourapplication;
    }
    location @yourapplication {
        gzip            on;
        gzip_buffers    8 256k;

        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-Protocol $scheme;
		
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;

	}

    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/str.wiki/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/str.wiki/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
server {
    if ($host = str.wiki) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    listen 80;
    server_name str.wiki 165.232.151.84;
    return 404; # managed by Certbot


}
```

units/myapp.service (systemd)
```
[Unit]
Description=gunicorn uvicorn service for pysidian/blog API and static server
After=syslog.target

[Service]
User=curtis
WorkingDirectory=/apps/blog
#Environment="PATH=/apps/venv/bin"
ExecStart=/apps/venv/bin/gunicorn -b 127.0.0.1:8000 -w 4 -k uvicorn.workers.UvicornWorker main:api --name blog_svc --chdir /apps/blog/ --access-logfile /apps/logs/blog_api/access.log --error-logfile /apps/logs/blog_api/errors.log --preload --reload
#RestartPreventExitStatus=1
#SuccessExitStatus=2
#RestartForceExitStatus=3 4

# \/ \/ <- Added post recording for better restart perf.
ExecReload=/bin/kill -s HUP $MAINPID
KillMode=mixed
TimeoutStopSec=5
PrivateTmp=true
# /\ /\ <- Added post recording for better restart perf.

# Requires systemd version 211 or newer
RuntimeDirectory=apps/blog/
RuntimeMaxSec=604800
Restart=always
Type=notify
StandardError=syslog
NotifyAccess=all

[Install]
WantedBy=multi-user.target
```

--- 
### ... troubleshooting

```
systemctl stop blog
systemctl start blog
systemctl status blog

journalctl -u blog | less +G
journalctl -e
cat /apps/logs/blog_api/errors.log | less +G

nano /etc/systemd/system/blog.service
nano /etc/nginx/sites-enabled/blog.nginx

systemctl daemon-reload
service nginx restart
```
```
/apps/venv/bin/gunicorn -h 
```

```
ufw allow in on eth0 to any port 80 proto tcp
```

https://unix.stackexchange.com/questions/517759/how-to-fix-service-start-request-repeated-too-quickly-on-custom-service




SSL occurs on the uvicorn level, not here:
```
/apps/venv/bin/gunicorn -b 127.0.0.1:8000 -w 4 -k uvicorn.workers.UvicornWorker main:api --name blog_svc --chdir /apps/blog --access-logfile /apps/logs/blog_api/access.log --error-logfile /apps/logs/blog_api/errors.log # --certfile=/etc/letsencrypt/live/str.wiki/fullchain.pem --keyfile=/etc/letsencrypt/live/str.wiki/privkey.pem # -> either way, cannot read from here; see nginx for auto letsencrypt settings ->; can cp to local project to be able to read properly, but then looking for https://127.0.0.1:8000 from workers -> nginx 502 bad gateway
```
https://certbot.eff.org/docs/using.html#where-are-my-certificates

```
sudo snap install --classic certbot
sudo ln -s /snap/bin/certbot /usr/bin/certbot
sudo certbot --nginx -d mysite.com
```

```
chmod 0755 /etc/letsencrypt/
```


other issues:
- ModuleNotFoundError 'uvicorn.protocols'


```

```