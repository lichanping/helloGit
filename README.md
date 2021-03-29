# hello Git
## Git useful commands
1. git **clone**: clone a repository into new directory and everything up-to-date.
```bash
git clone https://github.com/lichanping/helloGit.git
```
2. git **branch**: View all local branches.
```bash
git branch
```
3. git **status**: View current status. Show nothing to commmit or changes to commit depending on modify status.
```bash
git status
```
4. git **add**: Add to staging area
```bash
echo create a file in working directory
echo print('hello world')>hello.py
git add hello.py
```
git **restore** --staged <file>: unstage the file if added unintentionally.
5. git **commit**: Record changes to the repository. The files become unmodified after commit.
```bash
git commit -m "add py file"
```
6. git **checkout**: Switch branches to local dev branch for create a new pull request
```bash
git checkout -b dev
echo print('local dev branch')>dev.py
git add .
git commit -m "new code on dev branch"
git push "origin" dev 
```
7. git **log**: Show commit log
8. git **merge**: Fast-forward merge.
```bash
echo During development phase, my local branch dev is out-of-date, so need to merge latest code from main branch.
git checkout main
git pull
git checkout dev
git merge main
```
9. git **pull**: pull back commits of remote repository, different from fetch.
```bash
git pull
```
10. Remote code rollback process
```bash
git checkout main #Switch to the target branch
git pull
git branch main_backup #backup everything
git revert <commitID> #Undo the specified version
git commit -m "revert the wrong commit"
git push
```
The difference between git revert and git reset<br>
*git revert rolls back the previous commit with a new commit, while git reset directly deletes the specified commit.
In the case of git reset, the effect is similar. However, there is a difference when you continue to merge older versions later. Because git revert "neutralizes" the previous commit with a reverse commit, when the old branch is merged later, the changes will not reappear. branch is merged again, these rolled back commits should be brought back in.
git reset moves the HEAD back a bit, while git revert moves the HEAD forward, except that the content of the new commit is the opposite of the content to be reverted, offsetting the content to be reverted.*
