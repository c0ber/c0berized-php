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
bound port to host 3306

MYSQL_ROOT_PASSWORD: 1234
MYSQL_DATABASE: symfony
MYSQL_USER: symfony
MYSQL_PASSWORD: symfony
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
port bound to host 80
linked: php
volumes bound:
    ./code -> /app
    ./Docker/nginx/nginx.conf -> /etc/nginx/conf.d/default.conf
    ./Docker/nginx/logs/ -> /var/log/nginx/
```
