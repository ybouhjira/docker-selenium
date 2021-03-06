# Selenium in a docker container
## docker-compose
```yaml
selenium-hub:
    restart: always
    image: ybouhjira/selenium-hub
    ports:
        - "8000:4444"
    environment:
        - "TIMEOUT=120"
        - "CLEAN_UP_CYCLE=120"
firefox-node:
    restart: always
    image: ybouhjira/selenium-firefox-node
    links:
        - selenium-hub
    environment:
        - "MAX_INSTANCES=10"
        - "MAX_SESSION=10"
chrome-node:
    restart: always
    image: ybouhjira/selenium-chrome-node
    links:
        - selenium-hub
    environment:
        - "MAX_SESSION=10"
        - "MAX_INSTANCES=10"
    volumes:
        - /dev/shm:/dev/shm # fixes a chrome bug
```

## Webdrier.io settings
```json
{
    "chrome": {
        "desiredCapabilities": {    
            "browserName": "chrome",
            "chromeOptions": {
                "args": [
                    "window-size=1366,768", 
                    "hide-scrollbars", 
                    "headless",
                    "no-sandbox",
                    "disable-gpu",
                    "user-agent=\"Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/60.0.3112.101  Safari/537.36\""                
                ],
                "excludeSwitches": ["ignore-certificate-errors"]
            }
        }
    },
    "firefox": {
        "desiredCapabilities": {    
            "browserName": "firefox",
            "moz:firefoxOptions": {
                "args": ["-headless"]
            }
        }
    }
}
```
