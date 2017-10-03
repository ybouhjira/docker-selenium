FROM ubuntu:16.04
LABEL "maintainer"="ybouhjira"

RUN mkdir /app && \
    cd /app && \ 
    apt-get update && \
    apt-get install wget unzip openjdk-8-jre -y && \
    wget https://goo.gl/21wWg8 && \
    wget https://chromedriver.storage.googleapis.com/2.32/chromedriver_linux64.zip && \
    unzip chromedriver_linux64.zip && \
    mv chromedriver /usr/bin && \
    apt-get remove unzip wget -y && \
    apt-get autoremove

EXPOSE 4444
RUN mv /app/21wWg8 /app/selenium-server-standalone-3.6.0.jar
CMD cd /app && java -jar selenium-server-standalone-3.6.0.jar -role hub
