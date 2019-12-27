FROM java:8-jdk

COPY apache-tomcat-9.0.24.tar.gz /
COPY pinpoint-collector-1.8.4.war /

RUN tar zxvf /apache-tomcat-9.0.24.tar.gz -C /usr/local/ && mv /usr/local/apache-tomcat-9.0.24 /usr/local/tomcat \
    && rm -rf /usr/local/tomcat/webapps/** \
    && unzip /pinpoint-collector-1.8.4.war -d /usr/local/tomcat/webapps/ROOT \
	&& sed -i "s/localhost/pinpoint-hbase/g" /usr/local/tomcat/webapps/ROOT/WEB-INF/classes/hbase.properties \
    && sed -i "s/localhost/pinpoint-hbase/g" /usr/local/tomcat/webapps/ROOT/WEB-INF/classes/pinpoint-collector.properties \
    && rm -rf /apache-tomcat-9.0.24.tar.gz \
    && rm -rf /pinpoint-collector-1.8.4.war

CMD ["/usr/local/tomcat/bin/catalina.sh", "run"]
