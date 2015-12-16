FROM registry.access.redhat.com/jboss-eap-6/eap-openshift:latest

EXPOSE 8080 8888

RUN curl https://github.com/jnordell/openshift/images/ticketmoster/ticket-monster.war -o $JBOSS_HOME/standalone/deployments/ticket-monster.war
