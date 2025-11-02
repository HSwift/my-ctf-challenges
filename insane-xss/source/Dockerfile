FROM node:18.6.0-alpine3.16

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/' /etc/apk/repositories && \
    apk update && \
    apk add --no-cache tini libexif zlib-dev udev nss ca-certificates chromium openjdk11 && \
    adduser -h /app -D -u 1001 app

USER app
COPY src/apache-tomcat-9.0.40.tar.gz /tmp/apache-tomcat-9.0.40.tar.gz

RUN tar -xvf /tmp/apache-tomcat-9.0.40.tar.gz -C /app &&\
    rm -rf /app/apache-tomcat-9.0.40/webapps/ROOT &&\
    sed -i '167 i <Valve className="org.apache.catalina.valves.ErrorReportValve" showReport="false" showServerInfo="false" />' /app/apache-tomcat-9.0.40/conf/server.xml

COPY src/ROOT.war /app/apache-tomcat-9.0.40/webapps/ROOT.war
WORKDIR /app/apache-tomcat-9.0.40/
CMD tini -- bin/catalina.sh run