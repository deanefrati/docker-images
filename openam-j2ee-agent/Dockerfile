# to configure the webagent to protect apache run
# cd web_agents/apache22_agent/bin
# ./agentadmin --install --acceptLicense --useResponse /tmp/openam.properties 
# apachectl start

FROM tomcat7
MAINTAINER Dean Efrati <deanefrati@gmail.com>

RUN yum install -y unzip links

ADD Tomcat-v6-7-Agent-3.3.0.zip /tmp/openam-j2ee-agent.zip
ADD openam.properties /tmp/openam.properties
ADD pwd.txt /tmp/pwd.txt

WORKDIR /usr/local/tomcat

RUN unzip /tmp/openam-j2ee-agent.zip

