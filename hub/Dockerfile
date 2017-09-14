FROM ubuntu:16.04
LABEL "maintainer"="ybouhjira"

RUN mkdir /app && \
    cd /app && \ 
    apt-get update && \
    apt-get install wget unzip openjdk-8-jre -y && \
    wget http://selenium-release.storage.googleapis.com/3.5/selenium-server-standalone-3.5.3.jar && \
    wget https://chromedriver.storage.googleapis.com/2.32/chromedriver_linux64.zip && \
    unzip chromedriver_linux64.zip && \
    mv chromedriver /usr/bin && \
    apt-get remove unzip wget -y && \
    apt-get autoremove

EXPOSE 4444

CMD cd /app && java -jar selenium-server-standalone-3.5.3.jar -role hub -debug -timeout $TIMEOUT -cleanUpCycle $CLEAN_UP_CYCLE
