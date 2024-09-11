Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]; [[ regular_expressions ]]
Ref: 
Tags: #public 

--- 
```py
import re
```

--- 

re.search() -> None if not found
re.findall() -> \[\] if not found

if using a single group (), returns that group in a list only
if using multiple groups, return each group item in a tuple

example.txt
```
This is a text file.
It can be read by the os through
```
```py
with open(os.path.join(path, filename) as f:
print(f.read)
```
...
```

re **.compile()** -> matches
```py
import re

sentence = 'Start a sentence and then bring it to an end'
pattern = re.compile('sentence')
matches = pattern.search(sentence)
print(matches)
# <re.Match object; span=(8, 16), match='sentence'>

```

re.sub(p, repl, line)
replaces all instances of found pattern p with a string (line)

#### change contents of a line : 
```py # foo.txt
ignored

regexd

alsoig

heres more lines

thar be a line
```
```
import re

with open('foo.txt', 'r') as read_file:
	out_file = open('bar.txt', 'w')
	for line in read_file.readlines():
		line = re.sub(r'regexd', 'this line was changed', line)
		out_file.write(line)
```
``` # bar.txt
ignored

this line was changed

alsoig

heres more lines

thar be a line
```


re **.findall()**
```py
ex_str = """
Bill is 99 years old, and Chris is 56 years old.
Abe is 97, and his grandfather, Tim is 87.
"""

>>> ages = re.findall(r'\d{1,3}', ex_str)
>>> print(ages)
['99', '56', '97', '87']

>>> names = re.findall(r'[A-Z][a-z]*', exampleString)
>>> # starts at anything A-Z -> then anything 0 or more a-z, but as soon as a whitespace, period, comma, etc. -> will stop parce
>>> 
>>> print(names)
['Bill', 'Chris', 'Abe', 'Tim']
```

re **.split()**
```py
>>> reg_str = "Hello, World"
>>> reg_splt = re.split(r'(,)', reg_str)
>>> print(reg_splt)
['Hello', ',', ' World']
```

--- 



#### tabbed lines
```py
import re

NONTAB = r'^-(.*)'
TABBED = r'(\t)(.*)'

with open('tabbs.txt', 'r') as f:
	fi = f.readlines()
	for i, l in enumerate(fi):
		if re.match(NONTAB, l):
			print(i, 'nontabbed')
		if re.match(TABBED, l):
			print(i, 'tabbed')
```
``` # tabbs.txt

- professional communication:
	— Be on time - if going to be late, contact the customer
	— Actively listening - allow to describe problem in great detail; take notes if necessary
	— Clarify customer statements - ask open ended questions to narrow scope of problems
	— Maintain positive attitude / project confidence
	— Use proper language and avoid jargon, acronyms, and slang
	— Set and meet expectations/timeline and communicate status with customer
	— Be culturally sensitive
	— Use appropriate professional titles
	— Avoid distractions when working with customers
	— Avoid being judgemental
	— Avoid dismissing customer problems
	— Deal appropriately with customers’ confidential and private materials
	— Don’t argue with customers or be defensive
	— Follow up with customer later to verify satisfaction
	— Provide proper documentation on services provided
	— Offer different repair/replacement options
```
--- 
e.g.
#### simpletool.to_seconds()

```py
import re


def to_seconds(timestr):
	"""
	:param timestr: e.g. '1d3h27m54s'
	"""
	reg = r'(\d+)?d?(\d+)?h?(\d+)?m?(\d+)s'
	to_s = [86400, 3600, 60, 1]

	if (m := re.match(reg, timestr).groups()):
		ts = [int(x) for x in m if x]
		to_s = to_s[-len(ts):]
		t = sum([n*to_s[i] for i,n in enumerate(ts)])
		return t


def to_seconds(timestr):

	reg = r'(\d+d)?(\d+h)?(\d+m)?(\d+d)?(\d+s)?'
	to_s = {'d': 86400, 'h': 3600, 'm': 60, 's': 1}
	
	if (m := re.match(reg, timestr).groups()):
		ts = {x[-1]:int(x[:-1]) for x in m if x}
		t = sum([to_s[k]*ts[k] for k in ts.keys()])
		return t



print(to_seconds('1d3h27m54s'))
print(to_seconds('3h54s'))
print(to_seconds('3h27m54s'))
print(to_seconds('1d'))
```
--- 
```py
# re-write re.sub() with string indexing
import re

s = 'this is my stringyyy here to fix' 
r = 'stringyyy'
m = re.search(r, s)
sx = s[:m.span()[0]] # 'this is my '
sz = s[m.span()[1]:] # ' here to fix'
sy = 'string'
sn = sx + sy + sz

print(sn)
print(re.sub(r, sy, s))
```

--- 
w/ f-strings :

```py
>>> y = 'badgers'
>>> x = rf'^{y}'
>>> import re
>>> z = 'badgers are here'
>>> a = 'are badgers here'
>>> re.findall(x, z)
['badgers']
>>> re.findall(x, a)
[]
```