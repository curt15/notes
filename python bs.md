Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python fun]]

These are snippets from simpletools that don't have a home (but seemed worth keeping)

--- 
- #idea : a wrapper that reads the function for commented out print statements && ... you can't -> ... you can (prog/test.py)
- fix with: Try except -> func() ??

```py
# adding a new snippit. 
print("added!")
```



--- 



**jsontoxml.py**
```py
import json


def add_tab(thing):
	return(f'\t{thing}')


def remove_tab(thing):
	return thing[1:]


def jsontoxml(mydict, tabs='', _xml=''):
	""" """
	for k,v in mydict.items():
		if type(v) == dict:
			_xml += f'\n{tabs}<{k}>'
			_xml = jsontoxml(v, tabs=add_tab(tabs), _xml=_xml)
			_xml += f'\n{tabs}</{k}>'
			tabs = remove_tab(tabs)
			
		elif type(v) == list:
			_xml += f'\n{tabs}<{k}>'
			ks = k[:-1]
			tabs = add_tab(tabs)
			
			for ul in v:
				_xml += f'\n{tabs}<{ks}>{ul}</{ks}'

			tabs = remove_tab(tabs)
			_xml += f'\n{tabs}</{k}>'

		else:
			_xml += f'\n{tabs}<{k}>{v}</{k}>'

	return _xml


mydict = {
	'key1': 'val1',
	'key2': 'val2',
	'key3': {
		'subkey1': 'subval1',
		'subkey2': 'subval2'
		},
	'notable_values': ['val4-1', 'val4-2', 'val4-3']
	}

print(jsontoxml(mydict))

# <key1>val1</key1>
# <key2>val2</key2>
# <key3>
# 	<subkey1>subval1</subkey1>
# 	<subkey2>subval2</subkey2>
# </key3>
# <notable_values>
# 	<notable_value>val4-1</notable_value
# 	<notable_value>val4-2</notable_value
# 	<notable_value>val4-3</notable_value
# </notable_values>
```


--- 

**randgrid.py**
```py
from random import randint

def randrow(dim):
	row = []
	for i in range(dim):
		row.append(randint(0,9))
	return row


def randgrid(dim:int):
	"""
	param dim: cubed size of grid
	"""
	grid = []
	for i in range(dim):
		grid.append(randrow(dim))
	return grid


mygrid = randgrid(10)
for row in mygrid:
	print(row)
```

--- 
**metricconv.py**
```py
def metricconv(val, unit_in, unit_out):
	"""
	Convert metric units of the same type via KHDudcm
	"""
	SI = {' ':1.0, 'k':1000, 'H':100, 'D':10, 'd':0.1, 'c':0.01, 'm':0.001}

	if len(unit_in) == 1:
		unit_in = ' {}'.format(unit_in)
	if len(unit_out) == 1:
		unit_out = ' {}'.format(unit_out)

	return val*SI[unit_in[0]]/SI[unit_out[0]]

print('')
print(convert_si(1, 'm', 'km'))
print(convert_si(1, 'km', 'm'))
print(convert_si(1, 'cm', 'm'))
```

--- 

**sumof.py**

```py
def sum_of(num):
	"""
	Returns the sum of all (+1) intervals from 0 --> num
		>>> sum_of(12)  # [0,1,2,3,4,5,6,7,8,9,10,11,12]
			78
	"""
	to_sum = []
	final = 0

	for i in range(num+1):
		to_sum.append(i)
		the_sum += i
	#print(to_sum)

	return final
```

**intintervals.py**

```py
def intintervals(ints: list, singlestep=False: int):
	"""
	Returns list(s) of (+1) steps between integers of a given list

		>>> func([0, 5, 12, 20, 26, 36, 45, 52, 62, 71, 77, 84, 93, 100])
		[1, 2, 3, 4]
		[6, 7, 8, 9, 10, 11]
		[13, 14, 15, 16, 17, 18, 19]
		[21, 22, 23, 24, 25]
		[27, 28, 29, 30, 31, 32, 33, 34, 35]
		[37, 38, 39, 40, 41, 42, 43, 44]
		[46, 47, 48, 49, 50, 51]
		[53, 54, 55, 56, 57, 58, 59, 60, 61]
		[63, 64, 65, 66, 67, 68, 69, 70]
		[72, 73, 74, 75, 76]
		[78, 79, 80, 81, 82, 83]
		[85, 86, 87, 88, 89, 90, 91, 92]
		[94, 95, 96, 97, 98, 99]

	param singlestep: starting index to make steps from 
		>>> func([0, 5, 12, 20, 26, 36, 45, 52, 62, 71, 77, 84, 93, 100], 0)
			[1, 2, 3, 4]
	"""

	for idx, element in enumerate(intlist[:-1]):
		if type(startidx) == int:
			return list(range(intlist[startidx] + 1, intlist[startidx+1]))
		else:
			return list(range(intlist[idx] + 1, intlist[idx+1]))
```

--- 

**CoordandPOI.py**

```PY
from collections import namedtuple

class Coord(namedtuple('Coord', ['x', 'y', 'z'])):
	"""
	Represents a set of points w/in a three-dimensional grid of cubes
	following the 'right-hand rule' of mathematics & physics.

			-Z
		._ _ _ _ _.
		:	 :	  :
		:	 :	  :
	-X	:----:----:	-X
		:	 :	  :
		:	 :	  :
		:- - - - -:
			+Z

	:param x: Longitude = west/east (-/+)	>>> co[0]
	:param y: Elevation = altitude			>>> co[1]
	:param z: Latitude = south/north (+/-)	>>> co[2]
	"""
	def __new__(cls, x, z, y=None):
		ynone = -3
		if not y:
			obj = super().__new__(cls, x, ynone, z)
			setattr(obj, 'y_auto', True)
		else:
			obj = super().__new__(cls, x, z, y)
			setattr(obj, 'y_auto', False)
		return obj

	def __call__(self):
		print('allowed.')


class POI(Coord):
	"""
	a Point of Interest
	"""
	def __init__(self, x, y, z):
		self.x = x
		self.y = y
		self.z = z
```

--- 

**forij.py**

```py
for i in range(10):
	for j in range(10):
		print(i,j)

# ... 
# 0 0
# 0 1
# 0 2
# 0 3
# 0 4
# 0 5
# 0 6
# 0 7
# 0 8
# 0 9
# 1 0
# 1 1
# 1 2
# 1 3
# 1 4
# 1 5
# 1 6
# 1 7
# 1 8
# 1 9
# 2 0
# 2 1
# 2 2
# 2 3
# 2 4
# 2 5
# 2 6
# 2 7
# 2 8
# 2 9
# 3 0
# 3 1
# 3 2
# 3 3
# 3 4
# 3 5
# 3 6
# 3 7
# 3 8
# 3 9
# 4 0
# 4 1
# 4 2
# 4 3
# 4 4
# 4 5
# 4 6
# 4 7
# 4 8
# 4 9
# 5 0
# 5 1
# 5 2
# 5 3
# 5 4
# 5 5
# 5 6
# 5 7
# 5 8
# 5 9
# 6 0
# 6 1
# 6 2
# 6 3
# 6 4
# 6 5
# 6 6
# 6 7
# 6 8
# 6 9
# 7 0
# 7 1
# 7 2
# 7 3
# 7 4
# 7 5
# 7 6
# 7 7
# 7 8
# 7 9
# 8 0
# 8 1
# 8 2
# 8 3
# 8 4
# 8 5
# 8 6
# 8 7
# 8 8
# 8 9
# 9 0
# 9 1
# 9 2
# 9 3
# 9 4
# 9 5
# 9 6
# 9 7
# 9 8
# 9 9
```

--- 

**ftprint.py**
```py
"""
"Fancy Terminal Prints" -- functions used to adjust pretty printing based on cli
"""
import os

def hbreak(symb='*':str, x=1, wdth=os.get_terminal_size().columns):
	"""
	Print a horizontal break across the CLI

	:param symb: the symbol to iterate
	:param x: the number of times to run
	:param wdth: desired width
	"""
	hbk = ''
	for p in range(wdth):
		hbk = hbk + symb

	if x > 1:
		print(hbk)
		hbreak(symb=symb, x=x-1, wdth=wdth)
	else:
		return print(hbk)

hbreak(x=10)
```

--- 
**codewars.py**

```py
def runthis():
	while True:
		print('this')

# runthis()

def solution(number):
	sols = []
	nums = [n for n in range(3, number)]
	for n in nums:
		if n % 5 == 0 or n % 3 == 0:
			print(n)
			# nums.remove(n)
			sols.append(n)
			
	return sum(sols)
	
# print(solution(10))


def find_it(seq):
	num_ct = {n: seq.count(n) for n in seq}
	for k,v in num_ct.items():
		if num_ct[k] % 2 != 0:
			return k

# print(find_it([20,1,-1,2,-2,3,3,5,5,1,2,4,20,4,-1,-2,5]))

def validate_pin(pin):
	for d in pin:
		try:
			int(d)
		except ValueError:
			return False
	return (len(pin) in (4,6))

# print(validate_pin('44b4'))

# import re
import string
def printer_error(s):
	err_ls = list(string.ascii_lowercase[13:])
	n = 0
	for l in s:
		if l in err_ls:
			n += 1

	return '{}/{}'.format(n,len(s))


s="aaaaaaaaaaaaaaaabbbbbbbbbbbbbbbbbbmmmmmmmmmmmmmmmmmmmxyz"
print(printer_error(s))
import subprocess
# print(subprocess.run(['which', 'python'], capture_output=True))


# Test.assert_equals(pig_it('Pig latin is cool'),'igPay atinlay siay oolcay')
# Test.assert_equals(pig_it('This is my string'),'hisTay siay ymay tringsay')

def pig_it(text):
	return ' '.join([wd[1:]+wd[0]+'ay' if wd.isalpha() else wd for wd in text.split(' ')])
# print(pig_it('This is my string'))


import string
def alphabet_position(text):
	alpha_pos = {l:i+1 for i,l in enumerate(list(string.ascii_lowercase))}
	return ' '.join([str(alpha_pos[l.lower()]) for l in text if l.isalpha()])

# print(alphabet_position("The sunset sets at twelve o' clock."))



# a = ["NORTH", "SOUTH", "SOUTH", "EAST", "WEST", "NORTH", "WEST"]
# # test.assert_equals(dirReduc(a), ['WEST'])
# def dirReduc(arr):
# 	# NS = ("NORTH", "SOUTH")
# 	# EW = ()
# 	dirs = {"x": ("EAST", "WEST"), "y": ("NORTH", "SOUTH")}

# 	fin_dirs = []
# 	moves = 0
# 	for i,d in enumerate(arr):
# 		try:
# 			if len(arr) > 1:
# 				for k,v in dirs.items():
# 					print(dirs[k])

# 					if arr[i] and arr[i-1] in dirs[k]:
# 						moves += 1

# 						# pass

# 						print(arr[i])
# 						print(arr[i-1])
# 						# arr.pop(i)
# 						# arr.pop(i-1)
						
# 					else:
# 						fin_dirs.append(arr[i])
# 						# fin_dirs.append(arr[i])
						
# 		except IndexError:
# 			pass

# 	if moves:
# 		dirReduc(fin_dirs)
	# return fin_dirs


# print(dirReduc(a))

def queue_time(customers, n):
    if n >= len(customers):
    	return max(customers)
    else:
    	return int(round(sum(customers)/n))
print(queue_time([2,2,3,3,4,4], 2))
    	
print(queue_time([1,2,3,4,5], 100))


def count_smileys(arr):
	faces = [(':',';'),('-','~'), (')', 'D')]
	for i,p in enumerate(arr):
		if p in faces[i]
    
    return #the number of valid smiley faces in array/list




```
