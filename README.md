# dockerDev (Nginx/Apache, PHP, MySQL)


# Presentation

* Source code in /www

* Persisted database in a volume

* Services (Apache, php,...) in /Docker


## How To Use this stack
    1) Configuration

    2) Use the stack

    3 ) Tools available ( shortcuts )


## 1) Configuration
    1.1) Php (ssmtp)

    1.2) Apache 2.4

    1.3) Mysql 

### 1.1  ssmtp (to use mail() function in php)

Don't forget ton configure ssmtp credentials inside the file "ssmtp.conf" (to create)

cp docker/php/ssmtp.conf.dist docker/php/ssmtp.conf
vim docker/php/ssmtp


### 1.2 Override Apache config and/or Add a vhost

You can change the main apache config file by editing this file : "httpd.conf"

vim docker/apache/httpd.conf



To add a vhost ( virtual host ), edit the file "httpd-vhosts.conf"

vim docker/apache/httpd-vhosts.conf


### 1.3) Override Mysql configuration

You can add / edit all mysql options ( my.cnf ), inside this file "conf-mysql.cnf"

vim docker/mysql/conf-mysql.cnf





## 2) Use the stack

Start (Builds, (re)creates, starts, and attaches to containers based on docker-compose.yml): 
```
docker-compose up -d
```

**Access to the website**:
```
docker-machine ip
```
http://<ip>:8080


Logs (Display containers logs (More logs in front/logs))
```
docker-compose logs
```

Stop (Stops running containers without removing them.)
```
docker-compose stop
```

They can be started again with ```docker-compose start```.

Delete (Removes stopped service containers)
```
docker-compose rm
```

#### Add a New Website
* create a folder in www
* create a virtual-host



## 3) Tools

# cleanenv.sh : 

- Remove stopped container

# logs.sh : 

- show the real time logs from the container "http"

# stats.sh :

- show the ressources statistics foreach running containers

# dump_sql.sh <database name>

- Create a dump of the database <database name> inside the current directory "tools/"

# restore_sql.sh <dump file.sql>

- Restore/import the sql dump inside the SQL container . 
