# Mysql

cd mysql


docker build -t docker-mysql --no-cache .


docker run -d -p 50001:3306 docker-mysql



mysql -h 0.0.0.0 -P 50001 -uroot -p1

or 

mysql -h 0.0.0.0 -P 50001 -u reactor -pp@ssword

use reactor;

show tables;
