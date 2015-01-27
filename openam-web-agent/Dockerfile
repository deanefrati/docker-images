# to configure the webagent to protect apache run
# cd web_agents/apache22_agent/bin
# ./agentadmin --install --acceptLicense --useResponse /tmp/openam.properties 
# apachectl start

FROM centos:centos6 
MAINTAINER Dean Efrati <deanefrati@gmail.com>

RUN yum install -y java7 httpd unzip links

ADD Apache-v2.2-Linux-64-Agent-3.3.3.zip /tmp/openam-web-agent.zip
ADD openam.properties /tmp/openam.properties
ADD pwd.txt /tmp/pwd.txt

WORKDIR /etc/httpd

RUN unzip /tmp/openam-web-agent.zip 

EXPOSE 80
