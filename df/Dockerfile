FROM ubuntu:18.04 as bld
RUN apt-get update
RUN apt install openjdk-11-jdk -y
RUN apt install git -y
RUN apt install maven -y
RUN git clone https://github.com/TrSverre/lesson12rep.git -b master
#RUN cd lesson12rep/
RUN mvn -f lesson12rep/pom.xml package

FROM tomcat:9.0.8-jre8-alpine
COPY --from=bld lesson12rep/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war /usr/local/tomcat/webapps
COPY --from=bld lesson12rep/WebContent/Config.properties /usr/local/tomcat/ROOT/