FROM debian:buster

RUN	apt-get -y update && apt-get -y install nginx
COPY tools/ /etc/ssl/
COPY conf/ /etc/nginx/sites-available
CMD ["nginx", "-g", "daemon off;"]