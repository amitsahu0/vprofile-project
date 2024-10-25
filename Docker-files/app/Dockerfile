FROM openjdk:11 as BUILD 
RUN apt update && apt install maven -y
RUN git clone https://github.com/amitsahu0/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install


FROM tomcat:9.0.96-jre21-temurin
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["cataline.sh","run"]