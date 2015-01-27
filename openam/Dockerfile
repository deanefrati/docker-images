FROM tomcat8 
MAINTAINER Dean Efrati <deanefrati@gmail.com>

ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH

ADD OpenAM-12.0.0.war $CATALINA_HOME/webapps/openam.war
RUN sed -i "97i CATALINA_OPTS=\"-Xmx1024m -XX:MaxPermSize=256m\"" $CATALINA_HOME/bin/catalina.sh

EXPOSE 8080

CMD ["catalina.sh", "run"]
