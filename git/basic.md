# 基本操作

### 1、配置git config 用于告诉git你是谁？
```
a name git config --global user.name "My Name"
an email git config --global user.email "me@mail.org"
```
完成配置就可以试试其他操作了。

### 2、得到一个仓库：

#### 2.1 git init 将一个目录初始化为一个仓库,里面.git文件夹用于存放仓库的快照数据.
#### 2.2 git clone Url.克隆一个仓库的主分支到本地文件夹.
有仓库了可以对仓库做点什么了。
### 3、查看你的仓库状态

#### 3.1 git status 命令查看你的代码在缓存与当前工作目录的状态
```
$ git status
On branch master

Initial commit

nothing to commit (create/copy files and use "git add" to track)

$ echo "A dummy app listing ways to just say 'hello'" > README.md
```
需要注意的是在每一步，通过git status命令提供当前的存储库状态和上下文帮助的有用的概述。

#### 3.2 git diff 显示具体修改的内容
```
yaoguangdeMacBook-Pro:node-backend JJW$ git diff
diff --git a/server/model/invitation.model.js b/server/model/invitation.model.js
index e7d1f6e..3672d1e 100644
--- a/server/model/invitation.model.js
+++ b/server/model/invitation.model.js
@@ -70,7 +70,7 @@ const InvitationSchema = new Schema({
   },
   address: {
     type: String,
-    label: '地址',
+    label: '地址', 
     default: ''
   },
```
git diff可以理解为是git status的详情。

### 4、将修改的内容添加的缓存中和取消添加

#### 4.1  git add file 将文件添加到缓存中 多个文件可以空格隔开
#### 4.2  git add . 添加所以项目（不包括已删除的)
#### 4.3  git add -A 添加所有文件
#### 4.4  git reset 取消缓存已缓存的内容,当 git add 的时候缓存文件内容当想取消某个文件的缓存时候需要用： git reset HEAD -- file
```
$ git reset HEAD -- hello.rb 
Unstaged changes after reset:
M hello.rb
```

在提交快照的时候最好先git status
```
yaoguangdeMacBook-Pro:node-backend JJW$ git status
On branch 7-11-backendinvitation
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   server/api/invitation/invitation.controller.js

yaoguangdeMacBook-Pro:node-backend JJW$ 
```
此时已经将修改的文件加入到缓存中接下来进行存储。

### 5、 存储快照
#### 5.1 git commit －m 存储快照并提交注释,在此之前要git add 将内容写入缓存,下面有简化的命令。
#### 5.2 git commit－am ‘注释’ 将添加缓存和添加注释合并到一起。

### 6、对分支的操作

#### 6.1 git branch 列出本地可用的分支
     6.1.1 git branch (branchname) 创建新分支
	 6.1.2 git branch -d (branchname) 删除分支
	 6.1.3 git branch -r 可以用来查看远程分支
	 6.1.4 git branch -a 查看所有分支
#### 6.2 git checkout 切换分支
	 6.2.1 git checkout  (branchname) 切换到branchname分支
	 6.2.2 git checkout -b (branchname) 创建新分支，并立即切换到它
#### 6.3 git merge 将分支合并到你的当前分支
	 例如 git merge removals   将removals分支合并到当前分支
#### 6.4 git fetch 从远端仓库下载新分支与数据
	 用法：git fetch <远程主机名> <分支名> 
	 例如：$ git fetch origin master 取回origin主机的master分支
#### 6.5 git pull 从远端仓库提取数据并尝试合并到当前分支
	 用法： $ git pull <远程主机名> <远程分支名>:<本地分支名> 如果远程分支是与当前分支合并，则冒号后面的部分可以省略
	 例如： $ git pull origin dev 将主机origin的分支dev 与当前本地分支合并。
#### 6.6 git push命令用于将本地分支的更新，推送到远程主机
	 用法： $ git push <远程主机名> <本地分支名>:<远程分支名>
	 例如：$ git push origin master 如果省略远程分支名，则表示将本地分支推送与之存在"追踪关系"的远程分支（通常两者同名），如果该远程分支不存在，则会被新建。
	 $ git push origin :master 如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。
	 
	 $ git push origin :master
	 # 等同于
	 $ git push origin --delete master





