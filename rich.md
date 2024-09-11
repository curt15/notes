Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: [docs](https://rich.readthedocs.io/en/stable/introduction.html); [github](https://github.com/willmcgugan/rich)
- [Markdown](https://rich.readthedocs.io/en/stable/markdown.html)
- [Layout](https://rich.readthedocs.io/en/latest/layout.html)
- [Console](https://rich.readthedocs.io/en/latest/protocol.html)
- [markup link](https://rich.readthedocs.io/en/latest/markup.html?highlight=link#links)
- https://gist.github.com/egmontkob/eb114294efbcd5adb1944c9f3cb5feda
- https://iterm2.com/ Preferences -> Profiles -> "Run coprocess: " ```echo nano \1```
	- this only works for actual path links, file:/// uri's still open to default app...
	- https://github.com/willmcgugan/rich/blob/master/examples/fullscreen.py (panel system)
- [BUG - Live view flickering on Windows](https://github.com/willmcgugan/rich/issues/1024)

rich text in the terminal

--- 
... no luck color in Markdown
```
from rich.text import Text
from rich.highlighter import Highlighter

rainbow = RainbowHighlighter()
menu_header = Text('MENU : ', style="bold magenta")
for index in range(len(menu_header)):
	menu_header.stylize(f"color({randint(16, 255)})", index, index + 1)

menu_header = rainbow(menu_header)

class RainbowHighlighter(Highlighter):
	# https://rich.readthedocs.io/en/stable/highlighting.html
    def highlight(self, text):
        for index in range(len(text)):
			...
```


--- 
... no luck with Live 
```py
import time

import rich
from rich.console import Console
from rich.markdown import Markdown
from rich.layout import Layout
from rich.live import Live
from rich.prompt import Prompt
from rich.screen import Screen


@pass_nb
def _nb_console(nb=None):
	""" """

	layout = Layout()
	layout.split_row(
		Layout(name="left"),
		Layout(name="right"),
		)
	layout['left'].update(md)
	# layout['right'].visible = False

	# layout['upper'].visible = False

	rmd = _get_rich_note(nb.get("PYTHON"), nb)

	# layout = Screen(rmd)

	layout['lower'].update(rmd)
	with Live(layout, screen=True) as live: # redirect_stdout=False, redirect_stderr=False, screen=True, transient=True
		
		# live.console.print(x)
		# layout['upper'].update()

		# layout['upper'].update(live.console.input('prompt: '))

		# name = Prompt.ask("Enter your name: ")
		# rich.print(name)
		# layout.update(name)

		while True:
			time.sleep(1)
			# live.console.print(rmd)
			x = live.console.input(rmd) # 'prompt: '
			# layout['lower'].update(x)
			if ' --note=' in x:
				fn = x.split(' --note=')[1].strip('"')
				try:
					rmd = _get_rich_note(nb.get(fn), nb)
					live.console.print(rmd)


					layout['lower'].update(rmd)
				except:
					# layout['lower'].update(f'Failed to render note: {fn}')
					break
```


--- 

```pip install rich```

```py
>>> from rich import pretty
>>> pretty.install()
>>> ["Rich and pretty", True]
```

```py
console.input("What is [i]your[/i] [bold red]name[/]? :smiley: ")
```


--- 
getting flickering if not using screen=True






--- 
#### Live

```py
from rich.live import Live

with Live as live:
	while True:
		x = live.console.input('in: ')
		live.console.print(x)
```






--- 
```py
from rich import print
from rich.console import Console
from rich.markdown import Markdown

md = (text="")
rich.inspect(md)
```

```
from rich.console import Console

console = Console()
# or
console = Console(record=True)
# -> 
# avail @ 
# console.export_ ...

```

```print("Visit my [link=https://www.willmcgugan.com]blog[/link]!")```
```console.print('google', style='blue link https://google.com'```





--- 

https://rich.readthedocs.io/en/latest/markup.html?highlight=links
