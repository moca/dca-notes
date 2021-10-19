# Simple Nginx image
FROM ubuntu:bionic

ENV NGINX_VERSION 1.14.0-0ubuntu1.9 
# Version proposed on the course not longer works
# Check current version by running on contaniner : docker run -it ubuntu:bionic 

RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx=$NGINX_VERSION
# We cannot be sure that every apt-get update will be launch, 

WORKDIR /var/www/html
COPY index.html .


EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

STOPSIGNAL SIGTERM
HEALTHCHECK CMD curl localhost:80
