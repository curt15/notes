Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]

--- 
```py
import sqlite3
```
--- 
SQL = Structured English Query Language (“sequel”)

--- 

```sh
$ sqlite3 db.sqlite3
sqlite> select * from user;
```

--- 
```py

PY_SQL_TYPES = {
	str: "TEXT",
	int: "INTEGER",
	float: "REAL"
	
}

def create_table(name, feats):

	_command = f"""CREATE TABLE IF NOT EXISTS {name}
		({name.lower()}_id INTEGER PRIMARY KEY AUTOINCREMENT,
		start_date TEXT,
		end_date TEXT,)"""
	
	
	for f in feats:
		if isinstance(f, int):
			_comm
		
	
	c.execute()
```


--- 

sentdex
```py
import sqlite3
import time
import datetime
import random
import matplotlib
matplotlib.use('TkAgg')
import matplotlib.pyplot as plt
import matplotlib.dates as mdates
from matplotlib import style
style.use('fivethirtyeight')

conn = sqlite3.connect('tutorial.db')
c = conn.cursor()

def create_table():
	c.execute('CREATE TABLE IF NOT EXISTS stuffToPlot(unix REAL, datestamp TEXT, keyword TEXT, value REAL)')

def data_entry():
	c.execute("INSERT INTO stuffToPlot VALUES(1225123542,'2019-01-01', 'Python', 8)")
	conn.commit()
	c.close()
	conn.close()
	# wouldn't use sql to input data by hand like this

def dynamic_data_entry():
	unix = time.time()
	date = str(datetime.datetime.fromtimestamp(unix).strftime('%Y-%m-%d %H:%M:%S'))
	keyword = 'Python'
	value = random.randrange(0,10)
	c.execute("INSERT INTO stuffToPlot(unix, datestamp, keyword, value) VALUES (?, ?, ?, ?)",
		(unix, date, keyword, value)) # mysql uses %s vs "?"
	conn.commit()

def read_from_db():
	"""
	WHERE value=4 AND keyword='Python'
	SELECT keyword, unix, value, datestamp
	"""
	c.execute("SELECT * FROM stuffToPlot WHERE unix > 1548099854.90716") #populates cursor.
	#data = c.fetchall() # copies cursor pop. can use fetchone() for row.
	#print(data)
	for row in c.fetchall():
		print(row[0]) # can print all or table index

def graph_data():
	c.execute('SELECT unix, value FROM stuffToPlot')
	dates = []
	values = []
	for row in c.fetchall():
		#print(row[0])
		#print(datetime.datetime.fromtimestamp(row[0]))
		dates.append(datetime.datetime.fromtimestamp(row[0]))
		values.append(row[1])

	plt.plot_date(dates, values, '-') #'-' is line style
	plt.show()

def del_and_update():
	"""
	UPDATE-ing and DELETE-ing data in SQL is PERMINENT! No UNDOS!
	Use automated backups!
	"""
	c.execute('SELECT * FROM stuffToPlot')
	[print(row) for row in c.fetchall()] #one line for loop

	# c.execute('UPDATE stuffToPlot SET value=99 WHERE value=4') #99 and 4 can be a variable
	# conn.commit()

	# c.execute('DELETE FROM stuffToPlot WHERE value=99')
	# conn.commit()

	# rather than DELETE, maybe check first.
	c.execute('SELECT * FROM stuffToPlot WHERE value=2') # In MySQL can use LIMIT= to keep you as safe as possible
	print(len(c.fetchall()))


del_and_update()

# create_table() # create table once
# data_entry()
# for i in range(10):
# 	dynamic_data_entry()
# 	time.sleep(1) # only doing this to make datestamp go up a second
# read_from_db()

c.close()
conn.close()
"""
defining c and conn at the top opens connections,
best to close at the end vs in fxn like data_entry()
"""
```



--- 