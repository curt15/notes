Links: [[PROGRAMMING]] - [[TECHNOLOGY]]
Rel: [[nanorc]]; [[vi]]; [[emacs]]; [[macos]]; [[linux]]
Ref: https://www.nano-editor.org/docs.php
- repo: https://git.savannah.gnu.org/cgit/nano.git
- https://en.wikipedia.org/wiki/GNU_nano

```man nano```
```man nanorc```

--- 

[docs - nanorc](https://www.nano-editor.org/dist/latest/nanorc.5.html)

```brew install nano```
-> ```ls /usr/local/share/nano```
https://stackoverflow.com/questions/9642617/nano-syntax-highlighting-in-mac-os-x-10-7-lion#13959357
```bash
/bin/ls /usr/local/share/nano/*.nanorc | xargs -I {} echo 'include "{}"' >> ~/.nanorc
```
or pick certain individual
```echo 
ls /usr/local/share/nano
echo 'include "/usr/local/share/nano/python.nanorc"'
echo 'include "/usr/local/share/nano/markdown.nanorc"'
echo 'include "/usr/local/share/nano/json.nanorc"'
```

-> update [[sh profile]] (.zshrc, .bashrc, ...) w/
```
alias nano="/usr/local/Cellar/nano/5.8/bin/nano"
```

| | | 
| :--: | :--: | 
| esc+u | undo | 

