Links: [[ INDEX ]] - [[ PYTHON ]]

str is a \_\_builtin\_\_ *type*

--- 
#### methods 

- **.strip()**
removes white spaces (including tabs and newlines) from L & R of str

- **.splitlines()**
returns a list of lines, split at the line boundaries

- **.replace(mystr, with)**
if not using [[re]]gular expression (aka a direct "string to replace");
as there is no str.remove() method...
```py
>>> s = 'I want to remove this remove this'
>>> s.replace('remove this', '')
'I want to  '
```

```py
>>> a = '"The quotes are part of the string"'
>>> b = "I ain't gotta escape that"
>>> c = 'I cain\'t not escape that'
>>> d = "\"The quotes are part of the string\""
>>> d
'"The quotes are part of the string"'
>>> print(d)
"The quotes are part of the string"
>>> 
```