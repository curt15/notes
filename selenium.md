Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: [docs](https://selenium-python.readthedocs.io/); -> drivers (e.g. [geckodriver](https://github.com/mozilla/geckodriver/releases))

Selenium with Python (gui/browser automation)

--- 
```pip install selenium```

--- 

notes:
```
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

browser = webdriver. (‘PATH’)
browser.get(‘url’)
elem = browser.find_element_by_link_text(‘Download’)
elem.text
>>> ‘Download’
elem.get_attribute(‘href’)
>>> ‘url’
elem.click()
searchBar = browser.find_element_by_id(‘q’) [inspect element]

searchBar.send_keys(Keys.ENTER)


about:profiles
```

-> basics:
```
import os
from selenium import webdriver
# from selenium.webdriver.firefox.webdriver import FirefoxProfile

fp = webdriver.FirefoxProfile()


fp.set_preference("browser.download.folderList",2)
fp.set_preference("browser.download.manager.showWhenStarting",False)
fp.set_preference("browser.download.dir", os.getcwd())
fp.set_preference("browser.helperApps.neverAsk.saveToDisk","text/csv")

browser = webdriver.Firefox(firefox_profile=fp) # or driver 
browser.get('https://www.sample-videos.com/download-sample-csv.php')
browser.implicitly_wait(3)

button = browser.find_element_by_xpath("//a[@href='csv/Sample-Spreadsheet-10-rows.csv']")
button.click()

```







--- 

[[ python ]]