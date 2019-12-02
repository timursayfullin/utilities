FROM ubuntu:18.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y sudo openjdk-11-jdk && \
    apt-get install -y git curl gnupg maven


RUN useradd docker && echo "docker:docker" | chpasswd && adduser docker sudo

RUN git clone https://github.com/timursayfullin/dashboard-api /tmp/dashboard-api | echo "docker" && \
    cd /tmp/dashboard-api && \
    mvn package

RUN mkdir /var/dashboard-api/ && \
    mv /tmp/dashboard-api/target/dashboard-api.jar /var/dashboard-api/dashboard-api.jar

RUN sudo ln -s /var/dashboard-api/dashboard-api.jar /etc/init.d/dashboard-api

USER docker

#ENTRYPOINT service dashboard-api start
#CMD echo "docker" | sudo -S service dashboard-api start && bash
CMD java -jar /var/dashboard-api/dashboard-api.jar