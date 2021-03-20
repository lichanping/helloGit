# helloGit
## Git useful commands
1. git clone: clone a repository into new directory and everything up-to-date.
```bash
git clone https://github.com/lichanping/helloGit.git
```
2. git branch: View all local branches.
```bash
git branch
```
3. git status: View current status. Show nothing to commmit or changes to commit depending on modify status.
```bash
git status
```
4. git add: Add to staging area
```bash
echo create a file in working directory
echo print('hello world')>hello.py
git add hello.py
```
5. git commit: Record changes to the repository. The files become unmodified after commit.
```bash
git commit -m "add py file"
```
6. git checkout: Switch branches to local dev branch for create a new pull request
```bash
git checkout -b dev
echo print('local dev branch')>dev.py
git add .
git commit -m "new code on dev branch"
git push "origin" dev 
```
7. git log: Show commit log
8. git merge: Branch merging
```bash
echo During development phase, my local branch dev is out-of-date, so need to merge latest code from main branch.
git checkout main

git merge dev
```