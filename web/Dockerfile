FROM ubuntu:latest

RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -y install \
    vim apache2 php7.2 libapache2-mod-php7.2 php7.2-mysql php7.2-mbstring php7.2-common php7.2-xml php7.2-json php7.2-curl php7.2-zip

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
