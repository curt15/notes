Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[python 3rd party packages]]
Ref: [docs](https://www.crummy.com/software/BeautifulSoup/bs4/doc/), [lxml](https://lxml.de/)
Tags: #public 

Beautiful Soup
parsing HTML (for web scraping)

--- 

```py
pip install BeautifulSoup4
pip install lxml # need a parser 
```

--- 
```py
import bs4
```
```py
from bs4 import BeautifulSoup
```

--- 

```title = soup.title.text```

--- 

simplescrape.py
```
import bs4 as bs
import urllib.request

sauce = urllib.request.urlopen('https://www.crummy.com/software/BeautifulSoup/').read()

soup = bs.BeautifulSoup(sauce, 'lxml')

# print(soup.title)
# print(soup.title.text)
# print(soup.find_all('p')) #find all paragraph tags

# for paragraph in soup.find_all('p'):
# 	# print(paragraph.string) #works with a navigitable string (vs when there are child tags)
# 	print(paragraph.text)

# print(soup.get_text())


for url in soup.find_all('a'):
	print(url.get('href'))
```

navigatingtags.py
```
import bs4 as bs
import urllib.request

sauce = urllib.request.urlopen('https://pythonprogramming.net/').read()

soup = bs.BeautifulSoup(sauce, 'lxml')

nav = soup.nav

# print(nav)

# for url in nav.find_all('a'):
# 	print(url.get('href'))

# body = soup.body
# for paragraph in body.find_all('p'):
# 	print(paragraph.text)

for div in soup.find_all('div', class_='body'):
	print(div.text)

```

navigatingtables.py
```
import bs4 as bs
import urllib.request

sauce = urllib.request.urlopen('https://pythonprogramming.net/parsememcparseface/').read()

soup = bs.BeautifulSoup(sauce, 'lxml')

# # # table = soup.table #identical to below
table = soup.find('table')
# print(table)

table_rows = table.find_all('tr')

for tr in table_rows:
	td = tr.find_all('td')
	row = [i.text for i in td]
	print(row)

#BETTER TO USE PANDAS
"""
import pandas as pd

dfs = pd.read_html('URL', header=0)
for df in dfs:
	print(df)
"""
```

navigatingxml.py
```
import bs4 as bs
import urllib.request

sauce = urllib.request.urlopen('https://pythonprogramming.net/sitemap.xml').read()

soup = bs.BeautifulSoup(sauce, 'xml') #vs lxml

# print(soup)
for url in soup.find_all('loc'):
	print(url.text)
```

--- 

Dynamic Javascript Scraping (Sentdex) [ yt ](https://www.youtube.com/watch?v=FSH77vnOGqU):
https://pythonprogramming.net/javascript-dynamic-scraping-parsing-beautiful-soup-tutorial/




--- 
References:
- https://miningthedetails.com/blog/python/BeautifulSoupWebScraping/
- 




[[ python ]]