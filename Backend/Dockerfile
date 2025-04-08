# Use official Ubuntu base image
FROM ubuntu:latest

# Switch to root user
USER root

# Update the package list & install dependencies
RUN apt-get update -y && \
    apt-get install -y fontconfig openjdk-17-jre wget

# Dowload and extract Tomcat
WORKDIR /opt
RUN wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.102/bin/apache-tomcat-9.0.102.tar.gz && \
    tar -xvzf apache-tomcat-9.0.102.tar.gz && \
    rm apache-tomcat-9.0.102.tar.gz 

# Set the working directory to Tomcat
WORKDIR /opt/apache-tomcat-9.0.102

# Ensure shell scripts are executable
RUN chmod +x bin/*.sh

# Download and place the WAR file and MySQL connector
RUN wget https://s3-us-west-2.amazonaws.com/studentapi-cit/student.war -O webapps/student.war && \
    wget https://s3-us-west-2.amazonaws.com/studentapi-cit/mysql-connector.jar -O lib/mysql-connector.jar

# Copy the context.xml file
COPY context.xml conf/context.xml

# Expose the Tomcat port
EXPOSE 8080

# Start Tomcat (corrected)
CMD ["bin/catalina.sh", "run"]