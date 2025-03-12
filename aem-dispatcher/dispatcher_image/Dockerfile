FROM ubuntu:bionic

# Installi Apache
RUN apt-get update && apt-get install -y apache2

# Install required tools
RUN apt-get install -y curl && \
    apt-get install -y sudo && \
    apt-get install -y vim && \
    apt-get install -y wget && \
    apt-get install -y zip

# Copy dispatcher module and set permissions
COPY mod_dispatcher.so /usr/lib/apache2/modules/mod_dispatcher.so
RUN chmod 644 /usr/lib/apache2/modules/mod_dispatcher.so

# Copy dispatcher configuration
COPY dispatcher.any /etc/apache2/conf-enabled/dispatcher.any
COPY dispatcher.conf /etc/apache2/conf-available/dispatcher.conf
RUN a2enconf dispatcher

# Set correct permissions for web directory
RUN chown -R www-data:www-data /var/www/html

# Expose Apache HTTP port
EXPOSE 80

# Start Apache in foreground
CMD apachectl start && tail -F /var/log/apache2/error.log

# Clean Up apt Cache to Reduce Image Size
RUN rm -rf /var/lib/apt/lists/*