## Git

### 初始化

1. git init:初始化仓库
2. git remote add origin git@github.com:userName/repositoryName.git：与自己github服务器的特定仓库连接

### 上传已修改内容到git服务器

1. git add .:添加所有修改过的文件到暂存区
2. git commit -m “message”:将所有暂存区的文件保存到本地服务器
3. git push origin master：将本地的提交传送到远程github服务器



2. 使用*git init*可以初始化一个仓库：直接使用git init，将当前目录设置为git仓库，在目录下新建一个.git目录

2. git init gittest：在当前目录下创建一个gittest目录，将该gittest目录作为git仓库，在里面新建一个.git目录

3. 本地库与github连接： git remote add origin git@github.com:michaelliao/learngit.git

4. 将需要管理的文件放入仓库文件夹

5. 使用*git add <file>*添加文件进入暂存区（可连续添加多个）

6. git add **.**  :可以添加所有修改过的文件（.会匹配所有文件，但add只会添加被修改过的文件）

7. 提交到本地服务器head并备注信息：但最后需要*git commit -m “message”*

8. *git status* 可以看到仓库当前的状态（change表示仓库中文件修改了但还未add和commit）（即每次修改了文件，都需要add和commit）

9. *git diff* 可以看到文件具体修改了什么（显示方式为-（删掉了的内容），+（增加的内容））

10. *git log*：将输出日志，包括修改者、修改时间和修改后加的介绍

11. git add 实际上是将工作区中的修改放入 版本库.git中的缓存区stage，然后commit将缓存区中所有内容加入分支master中

12. git check out 使用版本库中的版本替换工作区的版本（工作区已删除也能替换）

13. ### *只要本地做了提交，就可以使用 git push origin master 将修改推送至GitHub*

14. 只有在工作区中才能执行git相关命令

15. git clone url：可以在当前目录下克隆目标仓库

16. git实现原理：每次向git系统提交一个版本，都会将这个版本完整地存储进git数据库

17. git数据库：