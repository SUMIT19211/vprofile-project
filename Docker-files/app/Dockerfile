FROM maven:3.9.9-eclipse-temurin-21-alpine-jammy AS BILD_IMAGE
RUN git clone https://github.com/SUMIT19211/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install


FROM tomcat:10.1.0-jdk21
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BILD_IMAGE /vprofile-project/target/vprofile.war /usr/local/tomcat/webapps/vprofile.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
