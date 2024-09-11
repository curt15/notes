Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[macos]]; [[linux]]; [[commands]]
Ref: 
Tags: #public 

--- 
grep - global regular expression print 

Global Regular Expression Print (the given string)

```sh
grep "this string"
```

```sh
grep . "import mypackage" *.py
```

find all urls within rtf files in the current directory:
```sh
grep -ho 'http[^ ]*' ./*.rtf > urls.txt
```

e.g.
```sh
grep ‘== None’ *.py

grep -R --include=\*.py 'Union' ./
```
