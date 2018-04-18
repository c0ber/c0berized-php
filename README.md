# c0berized-php
Docker config for php development

## Usage

###### Spawn dockers
```
make spawn
```


## Info

##### Note
> This is WIP, has some value probably, but requires some work to be done. Dont kill me before removing ***this*** note ;)
##### DB config
```
bound port to host env:MYSQL_PORT=3306
env:MYSQL_PORT=3306
env:MYSQL_ROOT_PASSWORD=1234
env:MYSQL_DATABASE_NAME=symfony
env:MYSQL_USER_NAME=symfony
env:MYSQL_USER_PASSWORD=symfony
```

##### PHP 
```
exposes port 9000 and 9001
linked: db
volume bound: 
    ./code -> /app
```

##### Nginx
```
port bound to host env:NGINX_PORT=80
linked: php
volumes bound:
    ./code -> /app
    ./Docker/nginx/nginx.conf -> /etc/nginx/conf.d/default.conf
    ./Docker/nginx/logs/ -> /var/log/nginx/
```
