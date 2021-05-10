# WebScraping Using Selenium

Web Scrapping also called “Crawling” is the technique to gather data automatically from an online source usually from a website.While Web Scrapping is an easy way to get a large volume of data in a relatively short time frame, it adds stress to the server where the source is hosted.
The Selenium API uses the WebDriver protocol to control a web browser, like Chrome, Firefox or Safari. The browser can run either localy or remotely.


While creating web-crawler scripts i faced many problems and i am going to address them with their solutions that worked for me:

1. We have to understand how web-crawler browser works what i mean is how it store xpath of diferent element and when it gets changed.
  * In single page scraping we never face this problem but while crawling multiple pages it gets change.
  * Whenever browser switch to different page and again get back to same page, all xpath gets change, so we have to make script by taking care of this. It helps us to save a lot of time
  
2. Sometimes tag are present in **iframe tag**, we can get their xpath easily but we will always get error.
  * To solve this we need to switch in iframe first than we can find the xpath of tag inside it.
  * **browser.switch_to.frame(browser.find_element_by_xpath("//iframe[@id='desgntool-iframe']"))**
  
3. Sometimes tag is present but still we get error:
  * we can use this, it solves this problem,  
  * **browser.find_element(By.XPATH, "//a[@href='/cart']")**
  * **browser.execute_script("arguments[0].click();", cart)**
  
