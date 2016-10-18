# Mysql

cd mysql


docker build -t docker-mysql --no-cache .


docker run -d -p 50001:3306 docker-mysql



mysql -h 0.0.0.0 -P 50001 -uroot -p1

or 

mysql -h 0.0.0.0 -P 50001 -u reactor -pp@ssword

use reactor;

show tables;


# Nginx 

mkdir ~/mount

cd nginx

docker build -t docker-nginx  --no-cache .

docker run -d -v ~/mount:/var/log/nginx  -p 80:80 docker-nginx

browser localhost

ls ~/mount   #check ~/monut with the log files


# Tomee

cd tomee

docker build -t docker-tomee  --no-cache .

docker run -d -p 8080:8080  docker-tomee

browser localhost:8080
