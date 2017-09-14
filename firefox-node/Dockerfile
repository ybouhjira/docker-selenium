FROM ubuntu:16.04
LABEL "maintainer"="ybouhjira"

RUN mkdir /app && \ 
    cd /app && \
    apt-get update && \ 
    apt-get install unzip wget openjdk-8-jre firefox libgconf-2-4 -y --allow-unauthenticated && \ 
    wget http://selenium-release.storage.googleapis.com/3.5/selenium-server-standalone-3.5.3.jar  && \ 
    wget https://github.com/mozilla/geckodriver/releases/download/v0.18.0/geckodriver-v0.18.0-linux64.tar.gz && \
    tar zxvf geckodriver-v0.18.0-linux64.tar.gz && \
    mv geckodriver /usr/bin && \ 
    chmod +x /usr/bin/geckodriver

EXPOSE 5555

CMD cd /app && java -jar selenium-server-standalone-3.5.3.jar \
    -role node \
    -maxSession $MAX_SESSION \
    -hub http://selenium-hub:4444/grid/register \
    -browser browserName=firefox,maxInstances=$MAX_INSTANCES

