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
git **restore** --staged <file>: to unstage the file if added unintentionally.
```bash
git restore --staged my_code.py
```
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

11. How to quickly shift to another work branch
```bash
git branch -m <newBranchName>
git pull origin <mainBranchName>
```
This will automatically pull all the latest code to main branch and merge into the renamed work branch.

12. Create a new branch based on main branch and Switch to it
```bash
switch to main branch and pull latest
git branch -b <newBranchName> 
```
13. 如果你有两个 GitHub 账号，而且你希望为每个账号使用不同的 SSH 密钥，你可以按照以下步骤进行设置
```bash
ssh-keygen -t rsa -C "your_email@example.com" -f ~/.ssh/id_rsa_personal # 生成两个 SSH 密钥对
ssh-add ~/.ssh/id_rsa_personal # 将 SSH 密钥添加到 SSH 代理
cat ~/.ssh/id_rsa_personal.pub | pbcopy # 复制公钥文件内容，用于添加到github中的ssh key
```
在 ~/.ssh/config 文件中添加配置，指定每个主机对应的密钥
```bash
# Personal account
Host github.com-personal
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa_personal
```
clone repo
```bash
git clone git@github.com-personal:<username>/<repoHost>.git
```
