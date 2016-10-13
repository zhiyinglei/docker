FROM ubuntu:14.04
MAINTAINER Zhiying 
RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install mysql-server

RUN DEBIAN_FRONTEND=noninteractive apt-get -y install wget
RUN wget "https://raw.githubusercontent.com/tascape/reactor/master/src/main/resources/db/reactor.sql" -O reactor.sql

RUN /etc/init.d/mysql start \
    && sleep 5 \ 
    && mysql -uroot -e "grant all privileges on *.* to 'root'@'%' identified by '1';" \
    && mysql -uroot -e "grant all privileges on *.* to 'root'@'localhost' identified by '1';" \  
    && mysql -u root -p1 -e "CREATE DATABASE reactor;"  \
    && mysql -u root -p1 -e "CREATE USER 'reactor'@'localhost' IDENTIFIED BY 'p@ssword';" \
    && mysql -u root -p1 -e "GRANT ALL ON reactor.* TO 'reactor'@'localhost';" \
    && mysql -u root -p1 -e "CREATE USER 'reactor'@'%' IDENTIFIED BY 'p@ssword';" \
    && mysql -u root -p1 -e "GRANT ALL ON reactor.* TO 'reactor'@'%';" \
    && mysql -u reactor -pp@ssword reactor < reactor.sql 


RUN sed -Ei 's/^(bind-address|log)/#&/' /etc/mysql/my.cnf \
    && echo 'skip-host-cache\nskip-name-resolve' | awk '{ print } $1 == "[mysqld]" && c == 0 { c = 1; system("cat") }' /etc/mysql/my.cnf > /tmp/my.cnf \
    && mv /tmp/my.cnf /etc/mysql/my.cnf

EXPOSE 3306
CMD ["/usr/bin/mysqld_safe"]


