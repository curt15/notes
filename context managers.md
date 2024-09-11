Links: [[ INDEX ]] - [[ PYTHON ]]
Rel: 
Ref: 
Tags: #public 


--- 

**open()**
- 'w' - will clear the previous file contents
```
ex_txt = 'Some Important Information:\nA New line!'

save_file = open('important.txt', 'w')
save_file.write(ex_txt)
save_file.close()
```
- 'a' - appends to bottom of file contents
```
ex_txt_add = '\nAnd then, Another New line of great importance!!'

save_file = open('important.txt', 'a')
save_file.write(ex_txt)
save_file.close()
```
- 'r' - read mode
	- .read() - returns a *str* of the full file contents
	- ```my_file = open('important.txt', 'r').read()```
	- .readlines() - returns a *list* of *str* separated at the line-breaks ('\\n')