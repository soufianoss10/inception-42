FROM debian:buster

#php extensions
RUN apt-get update && apt-get upgrade -y && apt install php-fpm \ 
    php-curl php-gd php-intl php-mbstring php-soap php-xml\
    php-xmlrpc php-zip wget -y
RUN docker-php-ext-install mysqli pdo_mysql

WORKDIR /var/www/html
#wordpress
RUN curl -O https://wordpress.org/latest.tar.gz && \
    tar -zxvf latest.tar.gz --strip-components=1 && \
    rm latest.tar.gz

RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

#set env var 4 db connection
ENV WORDPRESS_DB_HOST=mariadb
ENV WORDPRESS_DB_USER=root
ENV WORDPRESS_DB_PASSWORD=

#then, copying wdps config file into container
COPY wp-config.php /var/www/html/


EXPOSE 9000
# RUN wget https://wordpress.org/latest.tar.gz && tar -zxvf latest.tar.gz


CMD ["php-fpm", "-F"]