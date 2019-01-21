FROM centos-apache:1.0
MAINTAINER sankar <sankarapandi.u@lnttechservices.com>

# Create app directory
RUN mkdir -p /var/www/html/eams/

# change working dir to /var/www/html/eams/
WORKDIR /var/www/html/eams/

COPY . .

EXPOSE 80

# Simple startup script to avoid some issues observed with container restart
ADD run-httpd.sh /run-httpd.sh
RUN chmod -v +x /run-httpd.sh

CMD ["/run-httpd.sh"]



run-httpd.sh


#!/bin/bash

# Make sure we're not confused by old, incompletely-shutdown httpd
# context after restarting the container.  httpd won't start correctly
# if it thinks it is already running.
rm -rf /run/httpd/* /tmp/httpd*

exec /usr/sbin/apachectl -DFOREGROUND