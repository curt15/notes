Links: [[PROGRAMMING]]
Rel: 
Ref: https://git-scm.com/download/

--- 
installing git:
 https://git-scm.com/download/ -> pick OS (windows)
 [[homebrew]] - macos

 
 --- 
```git rm -r --cached templates/```
```git rm -r --cached static/```

...
https://stackoverflow.com/questions/10791315/git-how-to-recursively-delete-files-and-folders -> https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository
```
git filter-branch --index-filter 'git rm --cached --ignore-unmatch FILES' --prune-empty -- --all
```

--- 

```
git filter-branch -f --env-filter "GIT_AUTHOR_NAME='curt15'; GIT_AUTHOR_EMAIL='71923079+curt15@users.noreply.github.com'; GIT_COMMITTER_NAME='curt15'; GIT_COMMITTER_EMAIL='71923079+curt15@users.noreply.github.com';" HEAD
```
```
git remote add temp ../myproj/
git fetch temp
git merge temp/master --allow-unrelated-histories
git remote rm temp
```

--- 
```py
print(subprocess.run(['git', 'status'], capture_output=True))
if subprocess.run(['git', 'status'], capture_output=True).stderr == b'fatal: not a git repository (or any of the parent directories): .git\n':
	subprocess.run(['git', 'init'], capture_output=True)

# b'On branch master\n\nNo commits yet\n\nUntracked files:\n  (use "git add <file>..." to include in what will be committed)\n\tnoncommit.md\n\tobsidianparse.py\n\ttest.html\n\ttest.md\n\nnothing added to commit but untracked files present (use "git add" to track)\n'
```
--- 
github:
[github cheatsheet](https://training.github.com/downloads/github-git-cheat-sheet/)
https://github.com/simonw/simonw - self-updating profile readme guy
[github formatting]https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github
[GitHub Learning Lab](https://lab.github.com/)

--- 
https://www.git-scm.com/book/en/v2/Customizing-Git-Git-Configuration

https://softwareengineering.stackexchange.com/questions/80962/should-images-be-stored-in-a-git-repository

[Git Large File Storage](https://git-lfs.github.com/)

basic navigation:
```
git init
git status
git add -A
git commit -m ""


git reset
rm -rf .git


mkdir repo-cloning/
git clone .
```

github commits:
```
git config --list
git config --global user.name "John Doe"
git config --global user.email "johndoe@example.com"


git remote add origin https://github.com/
git remote rm origin
git branch -M master
git push -u origin master


# delete keychain github password to reset! ->
git commit --amend --reset-author
git push -u --force origin master

git credential-osxkeychain erase #->
host=github.com #->
protocol=https #->
#->
#->
```

.gitignore
```sh
.DS_Store

**__pycache__/**

*.sqlite3
*.sublime-project
*.sublime-workspace
*.pkl

*.py[co]

**/migrations/0*.py
```

[fork](https://docs.github.com/en/github/getting-started-with-github/fork-a-repo) - a server-side clone of a repository ("is a set of per-user branches")

contributing:
1. clone a repository into your own GitHub profile ("fork")
2. commit changes to the forked repo
3. make a [pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests)

- when you clone (anything) a remote called `origin` is created
- by default, any branches created from there track diff against `origin`
- fetch and merge changes from the `origin` upstream


--- 
get back a file deleted previously!
```sh
git log -3
# copy commit ID e.g. 7e835cf4a3109f2746f2a67629b045ec9cb5e2a7
# ->
git checkout 7e835cf4a3109f2746f2a67629b045ec9cb5e2a7 -- path/to/file.py
```

git push hangs after total line fix:
https://stackoverflow.com/questions/15843937/git-push-hangs-after-total-line

``` git config --global http.postBuffer 157286400 ```

--- 

References:
- https://stackoverflow.com/questions/6286571/are-git-forks-actually-git-clones
- 
