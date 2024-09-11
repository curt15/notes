Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]
Ref: 
Tags: #public 

--- 

```py
import csv
```

---

```py
with open('example.csv') as csvfile:
	my_data = csv.reader(csvfile, delimiter=',')
	# -> is a list of lists
	for row in my_data: 
		# row[0] = 
		# row[1] =
		
```