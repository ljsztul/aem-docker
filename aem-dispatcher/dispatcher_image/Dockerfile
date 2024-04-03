FROM ubuntu:bionic

# installing apache
RUN apt-get update && apt-get install -y apache2

# install other tools
RUN apt-get install -y curl && \
    apt-get install -y sudo && \
    apt-get install -y vim && \
    apt-get install -y wget && \
    apt-get install -y zip

ADD mod_dispatcher.so /usr/lib/apache2/modules/mod_dispatcher.so
RUN chmod 644 /usr/lib/apache2/modules/mod_dispatcher.so

ADD dispatcher.any /etc/apache2/conf-enabled/dispatcher.any
ADD dispatcher.conf /etc/apache2/conf-available/dispatcher.conf
RUN a2enconf dispatcher

RUN chown -R www-data /var/www/html

CMD apachectl start && tail -F /var/log/apache2/error.log
