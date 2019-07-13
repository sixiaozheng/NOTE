

# Git最佳实践

>   感谢廖雪峰老师的[Git教程](https://www.liaoxuefeng.com/wiki/896043488029600)
>   Git是目前世界上最先进的**分布式**版本控制系统。
>   Git是Linus用C语言开发的。
## Install Git
- Linux
    命令行安装：`$ sudo apt-get install git`
    source code 安装：
    ```bash
    # 下载后解压，然后依次输入以下命令
    ./config
    make
    sudo make install
    ```
- Windows
    1.  在[Git官网](https://git-scm.com/downloads)下载安装程序
    2.  在开始菜单里找到“Git”->“Git Bash”, 打开Git Bash后，在命令行输入：
        ```bash
        $ git config --global user.name "Your Name"
        $ git config --global user.email "email@example.com"
        ```

## Create repository

创建版本库，即创建一个目录，目录中的所有文件都可以被Git管理，每个文件的修改、删除都可以被Git跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

```bash
$ mkdir testgit
$ cd testgit/
$ git init
Initialized empty Git repository in D:/project/testgit/.git/
$ ls -a
./  ../  .git/
```

## Add file

```bash
$ touch test.py
$ git add test.py
$ git commit -m "create test.py"
[master (root-commit) 0ec0414] create test.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 test.py
```

## Change file

```bash
# 增加两行内容后
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   test.py

no changes added to commit (use "git add" and/or "git commit -a")

$ git diff
warning: LF will be replaced by CRLF in test.py.
The file will have its original line endings in your working directory
diff --git a/test.py b/test.py
index e69de29..c1e8e07 100644
--- a/test.py
+++ b/test.py
@@ -0,0 +1,2 @@
+import numpy as np
+print('xsc')

$ git add test.py
warning: LF will be replaced by CRLF in test.py.
The file will have its original line endings in your working directory

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   test.py
        
$ git commit -m "add two lines"
[master cc7fd88] add two lines
 1 file changed, 2 insertions(+)
 
$ git status
On branch master
nothing to commit, working tree clean
```

## 版本回退

```bash
$ git log
commit cc7fd8880015e22c1b1404431f62d958c8ad5a21 (HEAD -> master)
Author: ThinkToKnow <915480394@qq.com>
Date:   Sat Jul 13 19:55:33 2019 +0800

    add two lines

commit 0ec0414b288209aecda90a813f8a13b8a22a5e0e
Author: ThinkToKnow <915480394@qq.com>
Date:   Sat Jul 13 19:40:44 2019 +0800

    create test.py
# 在Git中，用HEAD表示当前版本
# 上一个版本就是HEAD^，上上一个版本就是HEAD^^,前10个版本 HEAD~100

# 回退到repo中HEAD的上一版本
$ git reset --hard HEAD^

# git reflog查看commit和reset的历史命令
$ git reflog
cc7fd88 (HEAD -> master) HEAD@{0}: reset: moving to HEAD^
8234385 HEAD@{1}: commit: add ndarray a
cc7fd88 (HEAD -> master) HEAD@{2}: commit: add two lines
0ec0414 HEAD@{3}: commit (initial): create test.py

# 利用git reflog查到commit id，可以实现版本往前
git reset --hard 8234385
```

## Working Directory and Stage

工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。

Git的版本库中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。

![git-repo](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

把文件往Git版本库里添加的时候，是分两步执行的：

第一步：用`git add`把文件添加进去，实际上就是把文件修改添加到`stage`；

第二步是用`git commit`提交更改，实际上就是把暂存区的所有内容提交到当前分支。

因为我们创建Git版本库时，Git自动为我们创建了唯一一个`master`分支，所以，现在，`git commit`就是往`master`分支上提交更改。

可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

## 管理修改

每次修改，如果不用`git add`到暂存区，那就不会加入到`commit`中。

每次`commit`，会将stage中所有的修改提交到repo.

## 撤销修改

-   当修改文件后，未`add`到stage时，此时`git status`查询状态

```bash
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   test.py

no changes added to commit (use "git add" and/or "git commit -a")

git checkout -- test.py
```



```bash
# 将working directory的修改撤销
git checkout -- <file>...
```

命令`git checkout -- test.py`意思就是，把`test.py`文件在工作区的修改全部撤销，这里有两种情况：

一种是`test.py`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`test.py`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。



-   如果修改已经`add`到`stage`中，此时`git status`查询状态

```bash
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   test.py

git reset HEAD test.py
```

## 删除文件

-   通过`rm`命令删除文件，与repo不一致，通过`git status`可以查看哪些文件被删除。如果要从repo中删除文件，应该通过`git rm`，然后`git commit`

```bash
$ git rm new.py
rm 'new.py'

$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        deleted:    new.py
        
$ git commit -m "delete new.py"
[master fa8e2d9] delete new.py
 1 file changed, 0 insertions(+), 0 deletions(-)
 delete mode 100644 new.py
```

**小提示**：先手动删除文件，然后使用`git rm <file>`和`git add<file>`效果是一样的。

-   **误删**，要恢复文件，相当于要撤销working directory的修改，使用`git checkout`

```bash
$ git checkout -- test.py
```

`git checkout`其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

**注意**：从来没有被添加到版本库就被删除的文件，是无法恢复的！

## Remote Repository（远程仓库）

1.  create SSH Key

    ```bash
    ssh-keygen -t rsa -C "youremail@example.com"
    ```

    在用户home目录下可以找到`.ssh`目录，其中`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥，可以放心地告诉任何人。

2.  登陆GitHub，打开“Account settings”，“SSH Keys”页面，然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴`id_rsa.pub`文件的内容，点“Add Key”，可以看到已经添加的Key。

## Add Remote Repository

1.  首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库：

2.  在Repository name填入`learngit`，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库：

3.  ```bash
    $ git remote add origin https://github.com/ThinkToKnow/NOTE.git
    ```

添加后，远程库的名字就是`origin`，这是Git默认的叫法，也可以改成别的。

4. ```bash
    # 由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
    $ git push -u origin master
    To https://github.com/ThinkToKnow/NOTE.git
     ! [rejected]        master -> master (fetch first)
    error: failed to push some refs to 'https://github.com/ThinkToKnow/NOTE.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    ```

    **问题原因**：远程库与本地库不一致造成的，在hint中也有提示把远程库同步到本地库就可以了。

    **解决办法**：

    ```bash
    git pull --rebase origin master
    ```

    该命令的意思是把远程库中的**更新合并**到（**pull=fetch+merge**）本地库中，**–-rebase**的作用是取消掉本地库中刚刚的commit，并把他们**接到**更新后的版本库之中。出现如下图执行pull执行成功后，可以成功执行git push origin master操作。

    ```bash
    $ git push origin master
    ```

5. git pull 失败 ,提示：fatal: refusing to [merge](https://www.centos.bz/tag/merge/) unrelated historiesgit 

    ```bash
    $ git pull origin master --allow-unrelated-histories
    ```

6. 以后本地修改后commit，就可以通过命令：

    ```bash
    $ git push origin master 
    ```

## Clone from remote repository

    ```bash
$ git clone https://github.com/ThinkToKnow/NOTE.git
    ```

Git支持多种协议，默认的`git://`使用ssh，但也可以使用`https`等其他协议。

使用`https`速度慢，每次推送都必须输入口令，但是在某些只开放http端口的公司内部就无法使用`ssh`协议而只能用`https`。

​     






## 命令快速检索区

```bash
# list available subcommands and some concept guides.
$ git help -a
$ git help -g

# to read about a specific subcommand or concept
$ git help <command>
$ git help <concept>

$ mkdir testgit
$ cd testgit/
$ git init
Initialized empty Git repository in D:/project/testgit/.git/

# 输出repo的状态
git status

# 查看修改后的文件跟repo中的文件不同之处
$ git diff
$ git diff HEAD <file>

# 撤销在working directory的修改,可以在误删文件时使用
$ git checkout -- <file>...

$ git add file1.txt
$ git add file2.txt file3.txt
$ git add . # add all file
$ git commit -m "add 3 files."

# 显示从最近到最远的commit日志
$ git log
$ git log --pretty=oneline # one commit，one line.

# 回到前一版本
$ git reset --hard HEAD^

# 查看commit和reset的历史命令
$ git reflog

# 将HEAD指向commit id对应的版本，用于从repo中不同的commit版本中恢复文件到working directory
$ git reset --hard <commit id>

# 添加remote repository
git remote add origin https://github.com/ThinkToKnow/NOTE.git

# 第一次push到remote repository
$ git push -u origin master

# 第一次push后，每次commit后，push到remote repository
$ git push origin master


```

