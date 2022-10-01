FROM php:7.4-apache

RUN docker-php-ext-install mysqli

RUN rm -rf /var/www/*
ADD src /var/www

ENV APACHE_RUN_USER www-data 
ENV APACHE_RUN_GROUP www-data 
ENV APACHE_LOG_DIR /var/log/apache2 
ENV APACHE_LOCK_DIR /var/lock/apache2 
ENV APACHE_PID_FILE /var/run/apache2.pid 

RUN echo "AddType application/x-httpd-php .html .htm" > /.htaccess 

EXPOSE 80

ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf


CMD /usr/sbin/apache2ctl -D FOREGROUND
