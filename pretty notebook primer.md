Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[prettynb]]
Ref: [github](https://github.com/prettynb/)

--- 


--- 

all notes within a specific "notebook" are required to have a unique name - because they can be directly referenced by **\[\[wiki link\]\]** to each other within any given note of the notebook. 

rather than creating a directory structure, and organizing this way (e.g. notes/school/science/Chapter 1 - The Scientific Method.docx), you can create table of content pages that point to specific notes:
\[\[SCHOOL\]\] -> \[\[SCIENCE\]\] -> \[\[Chapter 1 - The Scientific Method\]\].

better yet, you can make **\[\[The Scientific Method\]\]** it's own note, and then after this semester's science class, when the topic is bound to come up again, you could append to your same note and link the section in your current classes main note (\[\[SCIENCE 2\]\] -> \[\[The Scientific Method#Science 2\]\]).

because you'd get to any note by specifically reaching to open it by name (or by moving from a note you'd expected reference to it in), a flat directory structure is actually preferred. (e.g. notes/SCHOOL.md, notes/SCIENCE.md, notes/SCIENCE 2.md, notes/The Scientific Method.md, ... )

^^ this could seem like chaos when you're used to neatly nested folders, but instead of the information getting lost over the course of classes, books, chapters, etc. and blank slate -ing your notes every semester with a paper book or /new/class/folder, you keep your old snippits immediately accessible, which you can prune and move stuff to new note names over time. 

**links** can also additionally reference images in-line by **!\[\[mypic.png\]\]**. 

**tags** as \#tag are understood as being unique from the vanilla markdown: \# header 1, \`\`\`\#comments\`\`\` within **codeblocks**, and inside of **urls** such as https://en.wikipedia.org/wiki/Note-taking#Systems.

--- 

\[link\]
\[link | label \]
\[link#subhead\]
\[link#sub | label\]
\[l#sub | label \]

--- 

```bash
% mkdir notebook
% mkdir notebook/.pnbp
% cd notebook/.pnbp/
% python -m venv venv
% # ... 
% source venv/bin/activate
(venv) % 
(venv) % git clone https://github.com/prettynb/pnbp pnbp
(venv) % git clone https://github.com/prettynb/pnbp-blog blog
(venv) % cd pnbp/
(venv) % pip install -r requirements.txt
(venv) % cd ../blog/
(venv) % pip install -r requirements.txt
```

```powershell
C:\> mkdir notebook
C:\> mkdir notebook\.pnbp
C:\> cd notebook\.pnbp
C:\> python -m venv venv
C:\> # ...
C:\> .\venv\Scripts\activate
(venv) C:\> 
(venv) C:\> git clone https://github.com/prettynb/pnbp pnbp
(venv) C:\> git clone https://github.com/prettynb/pnbp-blog blog
(venv) C:\> cd pnbp
(venv) C:\> pip install -r requirements.txt
(venv) C:\> cd ..\blog
(venv) C:\> pip install -r requirements.txt
```

--- 

tasks
- [ ] laundry: towels
- [ ] water (amt: , )
- #todo deliver package to UPS 

--- 

```
mkdir /root/fakenb
mkdir /root/fakenb/imgs
mkdir /root/fakenb/html
mkdir /root/fakenb/venv
```

```
{
    "NOTE_PATH": "/root/fakenb",
    "IMG_PATH": "/root/fakenb/imgs",
    "HTML_PATH": "/root/fakenb/html",
    "VENV_PATH": "/root/venv",
    "API_BASE": "http://127.0.0.1:8000",
    "API_TOKEN": "None",
    "PUB_LNK_ONLY": false
}
```

--- 

**desired**:

N_HEADER
```
Links: 
Rel: 
Tags: 
Ref: 
```

#moc 
```
Links: [[INDEX]]
Rel: 
Tags: 
Ref: 
```
or
```
Links: 
Rel: 
Tags: #moc
Ref: 
```

#submoc
```
Links: [[PROGRAMMING]]
Rel: 
Tags: 
Ref: 
```
or
```
Links: [[PYTHON]]
Rel: 
Tags: #submoc 
Ref: 
```

--- 

crontab:
```sh
crontab -e 
```
```
# ... 
*/10 * * * * /users/alice/venv/bin/nb-git-commit-notebook
```

--- 

