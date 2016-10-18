# Set the base image to Ubuntu
FROM ubuntu

# File Author / Maintainer
MAINTAINER Zhiying

RUN apt-get update &&  \
    apt-get install -y \ 
	vim \
        nginx  

# Append "daemon off;" to the configuration file
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

# Expose ports
EXPOSE 80

# Set the default command to execute when creating a new container
CMD service nginx start
