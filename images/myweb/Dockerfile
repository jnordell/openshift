# Webserver container with CGI python script
# Using RHEL 7 base image and Apache Web server
# Version 1

# Pull the rhel image from the local repository
FROM rhel7:latest
USER user

MAINTAINER jnordell

# Fix per https://bugzilla.redhat.com/show_bug.cgi?id=1192200 
RUN yum -y install deltarpm yum-utils --disablerepo=*-eus-* --disablerepo=*-htb-* \
    --disablerepo=*-ha-* --disablerepo=*-rt-* --disablerepo=*-lb-* --disablerepo=*-rs-* --disablerepo=*-sap-*

RUN yum-config-manager --disable *-eus-* *-htb-* *-ha-* *-rt-* *-lb-* *-rs-* *-sap-* > /dev/null


# Update image
RUN yum update -y
RUN yum install httpd procps-ng MySQL-python -y

# Add configuration file
#ADD action /var/www/cgi-bin/action
#RUN echo "PassEnv DB_SERVICE_SERVICE_HOST" >> /etc/httpd/conf/httpd.conf
#RUN chown root:apache /var/www/cgi-bin/action
#RUN chmod 755 /var/www/cgi-bin/action
RUN mkdir -p /www/logs 
RUN mkdir -p /www/html
RUN chown -R apache:apache /www
RUN echo "The Web Server is Running" > /www/html/index.html
RUN sed -i '/ServerRoot/s_"/etc/httpd"_"/www/html"_' /etc/httpd/conf/httpd.conf
RUN sed -i 's/DocumentRoot "/var/www/html"/DocumentRoot "/www/html"' /etc/httpd/conf/httpd.conf
RUN echo "PidFile /www/httpd.pid" >> /etc/httpd/conf/httpd.conf
RUN sed -i 's/Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf
EXPOSE 8080

# Start the service
CMD ["-D", "FOREGROUND"]
ENTRYPOINT ["/usr/sbin/httpd"]

