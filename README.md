# Docker Hub: a Web Scraping Script
A Python script for web scraping dynamically the Docker Hub website and get a list of official and publisher-verified Images.

## Purpose
I needed to get a list of Docker Images, prossibly restricted to the Official and Verfidied-Publisher ones.
As result there will be created two json files that are arrays containing the list of the extraced docker images names, ready to be used like `docker pull <image_name>`.

## Dependencies
[Docker Hub]() is dynamically built so the only way for scraping it is to use Web Drivers. 
Selenium 4 is a great library that has generally a great support for Web Scraping, but greater when it comes to dynamic pages.

- [Selenium 4](https://www.selenium.dev/)
- [Web Driver Manager](https://github.com/SergeyPirogov/webdriver_manager)

## Usage
Download, solve dependencies, change local paths, configure your Web Driver (see below notes) and then Run.

### Important Notes
The scraping performing a url filtering: it scrapes all the images that are `Linux` and `Arm64` compatible platforms.

## Web Drivers
Web Drivers are essentially micro version of the browsers that can dialogue (and be managed) by external software, like Selenium 4. 
All browsers nowadays has Web Driver support, even Apple's Safari.

### Sfari Web Driver
macOS users, for once, are advantaged. You don't need to download anything, Safari WebDriver is already installed.
Thus, it needs to be activated: Run `safaridriver --enable`.
Just use the embedded Selenium's web driver:
`from selenium import webdriver` and then `driver = webdriver.Safari()`

### Chromium Browsers
All chromium based browsers need to download its WebDriver, that it must be compatible with the installed browser version. 
When it comes to Chromium based browsers, you'll need to configure its webdriver through Selenium. Quite annoying.
To avoid all of this, just use the Web Driver Manager python library that makes the works for you. It will update dynamically the web driver at each run, if it is requested.

In the source code there is one code line commented, that is a Microsoft Edge web driver working line using WDM:
`driver = webdriver.Edge(service=Service(EdgeChromiumDriverManager().install()))`
