to apply this config, follow these steps:
1. backup your original config file\
it's always good to have something to fall back on, so let's back it up. It's undes `/etc/nginx/nginx.conf`, something like this should do:
```
sudo mv /etc/nginx/nginx.conf /etc/nginx/nginxBACKUP.conf
```
2. use our config\
now, we can use our own config, ofc this command will need to be tweaked if you cloned the repo elsewhere (other than ~/)
```
sudo cp ~/nginx-playground/StaticWebServer/StaticWebServer.conf /etc/nginx/nginx.conf
sudo nginx -s reload
```