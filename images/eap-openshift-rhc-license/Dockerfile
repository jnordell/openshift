FROM registry.access.redhat.com/jboss-eap-6/eap64-openshift:1.1

EXPOSE 8080 8888

RUN echo "HC Bootcamp Middleware License" > $JBOSS_HOME/rhc-ose-license.txt
RUN echo "" >> $JBOSS_HOME/rhc-ose-license.txt
RUN echo "This software is meets the standard set forth by the company and can be used within all deployment environments" >> $JBOSS_HOME/rhc-ose-license.txt
