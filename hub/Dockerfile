FROM ubuntu:16.04
LABEL "maintainer"="ybouhjira"

RUN mkdir /app && \
    cd /app && \ 
    apt-get update && \
    apt-get install wget unzip openjdk-8-jre -y && \
    wget http://selenium-release.storage.googleapis.com/3.5/selenium-server-standalone-3.5.3.jar && \
    wget https://chromedriver.storage.googleapis.com/2.32/chromedriver_linux64.zip && \
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
    unzip chromedriver_linux64.zip && \
    mv chromedriver /usr/bin && \
    sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' && \
    apt-get install google-chrome-stable -y && \
    apt-get remove unzip wget -y && \
    apt-get autoremove

EXPOSE 4444

CMD cd /app && java -jar selenium-server-standalone-3.5.3.jar -role hub