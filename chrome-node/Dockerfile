FROM ubuntu:16.04
LABEL "maintainer"="ybouhjira"

RUN mkdir /app && \ 
    cd /app && \
    apt-get update && \ 
    apt-get install unzip wget openjdk-8-jre libgconf-2-4 -y --allow-unauthenticated && \ 
    sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' && \ 
    wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \ 
    apt-get update && \
    apt-get install google-chrome-stable -y && \
    wget http://selenium-release.storage.googleapis.com/3.5/selenium-server-standalone-3.5.3.jar  && \ 
    wget https://chromedriver.storage.googleapis.com/2.32/chromedriver_linux64.zip && \  
    unzip chromedriver_linux64.zip && \
    mv chromedriver /usr/bin && \ 
    chmod +x /usr/bin/chromedriver

EXPOSE 5555

CMD cd /app && java -jar selenium-server-standalone-3.5.3.jar \
   -role node \
   -maxSession $MAX_SESSION \
   -hub http://selenium-hub:4444/grid/register \
   -browser browserName=chrome,maxInstances=$MAX_INSTANCES

