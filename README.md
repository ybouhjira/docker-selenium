# Selenium in a docker container
## docker-compose
```yaml
selenium-hub:
    restart: always
    image: ybouhjira/selenium-hub
    ports:
        - "4444:4444"
chrome-node:
    restart: always
    image: ybouhjira/selenium-chrome-node
    links:
        - selenium-hub
    environment:
        - "MAX_INSTANCES=20"
        - "MAX_SESSIONS=20"
    volumes:
        - /dev/shm:/dev/shm # fixes a chrome bug
```

