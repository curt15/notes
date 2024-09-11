Links: [[TECHNOLOGY]]
Rel: [[vimtutor]]; [[nano]]; [[emacs]]
Ref: [home](https://www.vim.org/)
- [vimwiki](https://vimwiki.github.io/); https://nickjanetakis.com/blog/writing-and-previewing-markdown-in-real-time-with-vim-8
- vim surrounds - close brackets etc. 
- space vim - https://spacevim.org/

--- 

```
:help gs
```

--- 

EOF character replacement command (necessary when reading in a csv from Windows machine (seemed like even passing through a mail server (mac -> exchange -> open on mac) it would change the carriage return for CSV, visible by additional spacing between rows in macos MS Excel, etc. ))
```
: set ff=unix
: set ff=dos
```


--- 
vim syntax highlighting:
Ref: https://vim.help/06-using-syntax-highlighting
- https://stackoverflow.com/questions/25273075/editing-my-vimrc-file-on-a-mac
[[macos]] system vimrc @ ```/usr/share/vim/vimrc```

```bash
% cat /usr/share/vim/vimrc
" Configuration file for vim
set modelines=0		" CVE-2007-2438

" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
set nocompatible	" Use Vim defaults instead of 100% vi compatibility
set backspace=2		" more powerful backspacing

" Don't write backup file if vim is being called by "crontab -e"
au BufWrite /private/tmp/crontab.* set nowritebackup nobackup
" Don't write backup file if vim is being called by "chpass"
au BufWrite /private/etc/pw.* set nowritebackup nobackup

let skip_defaults_vim=1
```
can't overwrite ^^ 
->
```vi ~/.vimrc```
->
```bash
if &t_Co > 1
   syntax enable
endif
```

linux look for:
```~/.vimrc``` or ```/etc/vimrc```

--- 
