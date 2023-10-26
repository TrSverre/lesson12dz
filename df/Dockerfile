FROM ubuntu:18.04 as bld
RUN apt-get update
RUN apt install openjdk-11-jdk -y
RUN apt install git -y
RUN apt install maven -y
RUN git clone https://github.com/TrSverre/lesson12rep.git -b master
RUN cd Lesson12Rep/
RUN mvn package


FROM tomcat:9.0.8-jre8-alpine
COPY --from=bld Lesson12Rep/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps
COPY --from=bld Lesson12Rep/WebContent/Config.properties /usr/local/tomcat/ROOT/