Links: [[PYTHON]] - [[PROGRAMMING]]
Ref: https://docs.python.org/3/library/webbrowser.html

--- 

```py
import webbrowser

browser = webbrowser.get('firefox')
browser.open_new_tab('https://www.youtube.com')

```

--- 
e.g.
job search
```py
import webbrowser


def main():
	browser = webbrowser.get('safari')

	urls = ['lasvegas', 'sandiego', 'sfbay', 'denver', 'boulder', 'austin', 'chicago', 'newyork', 'boston']

	first = True
	for url in urls:
		browser.open_new_tab('https://{}.craigslist.org/search/spa'.format(url))
		#browser.open_new_tab('https://{}.craigslist.org/search/jjj?query=python'.format(url))

	webbrowser.open_new_tab('https://www.indeed.com')
	

if __name__ == '__main__':
	main()
```