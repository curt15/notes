Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: https://docs.python.org/3/howto/curses.html
- https://docs.python.org/3/howto/curses.html#attributes-and-color

--- 

```py
import time
import curses

# standard init: 
stdscr = curses.initscr() # the screen 

curses.curs_set(0)
curses.noecho()
curses.cbreak()
stdscr.keypad(True)


stdscr.addstr(15,5, "Hello")
stdscr.refresh()
time.sleep(3)


# standard breakdown:  
curses.curs_set(1)
curses.echo()
curses.nocbreak()
stdscr.keypad(False)

curses.endwin()


# ^^ must breakdown what you init, 
# 		or end up with stuff remaining in terminal 
# 		exit...
# or, the true standard: 
# curses.wrapper(func)



def main(stdscr):
	curses.curs_set(0)
	stdscr.addstr(15,5, "Hello")
	time.sleep(3)


curses.wrapper(main)




```


```
```