FROM openjdk:8 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone -b yannick https://github.com/yandjoumbi/java-hello-world-webapp.git
RUN cd java-hello-world-webapp && mvn install

FROM tomcat:8-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE java-hello-world-webapp/java-hello-world-webapp/target/java-hello-world.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]