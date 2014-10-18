FROM ubuntu:14.04
MAINTAINER Timothy Lim <tim@thewheatfield.org>
RUN apt-get update && apt-get install -y curl git apache2 php5 php5-mysql
WORKDIR /var/www

# https://github.com/jacksoncage/phppgadmin-docker
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_SERVERADMIN admin@localhost
ENV APACHE_SERVERNAME localhost

CMD /usr/sbin/apache2 -D FOREGROUND

EXPOSE 80
