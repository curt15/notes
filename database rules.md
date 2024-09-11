Links: [[PROGRAMMING]] - [[TECHNOLOGY]]

--- 

**Databases:**

1 NF = Make everything **atomic** (every cell contains a single value, not a list.); prohibits repeating group of columns (item1, item2,...,itemN)

2 NF = Remove partial dependancies; 1NF + every non-key column is fully dependent on the primary key

3 NF = removing transitive dependancies; 2NF + the non-key columns are independent of each others (i.e. the non-key columns are dependent on primary key, only on the primary key and nothing else.)

--- 

row = record (or tuple)
column = field (or attribute)

autoincrement the pk where new\_recork\_pk = current max value + 1