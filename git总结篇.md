## git

### git  config配置

​	git config  user.name 你的目标用户名

​	git config  user.email 你的目标邮箱名

​	使用--global参数，配置全局的用户名和邮箱，只需要配置一次即可。推荐配置github的用户名和密码

​	git config  --global user.name Jepson

​	git config  --global user.email jepsonpp@qq.com

### 	

###  查看配置信息

​	git config --list

### git  init

​	初始化git仓库

### git add

​	将文件从工作区添加到暂存区

#### 	分支语句

​		git add index.html   将文件index.html添加到暂存区
​		git add css    将css文件夹下的所有文件添加到暂存区
​		git add *.js    将所有的js文件添加到暂存区
​		git  add .   将所有的文件添加到暂存区
​		git  add -A   将所有的文件添加到暂存区
​		git  add --all   将所有的文件添加到暂存区

### git  commit 

​	将文件由暂存区	添加到仓库区
​		且生成版本号
​	git commit -m "提交申明"
​		如果不写提交说明，会进入vi编辑器，没有写提交说明，是提交不成功的。
​	git commit -a -m "提交说明"
​		 如果是一个已经暂存过的文件，可以快速提交，如果是未追踪的文件，那么命令将不生效。
​	git commit --amend -m "提交说明"
​		 修改最近的一次提交说明， 如果提交说明不小心输错了，可以使用这个命令

### git status

​	查看文件状态
​		红色表示工作区中的文件需要提交
​		绿色标识暂存区的文件需要提交

### git log

​	查看提交日志
​	git log --oneline  简洁的日志信息

### git  diff

​	可以查看每次提交的内容的不同
​	git diff  查看暂存区与工作区的不同
​	git diff --cached   查看暂存区与仓库区的不同
​	git diff HEAD   查看工作区与仓库区的不同,HEAD表示最新的那次提交
​	git  diff  版本号  版本号    查看两个版本之间的不同

### git reset

​	版本回退,将代码恢复到已经提交的某个版本中
​		git reset --hard  版本号
​	将版本回退到上一次提交
​		git reset --hard head~1
​			~1  上一次提交
​			~2上上次提交
​			~0  当前次提交
​	关于参数  --hard
​		git reset --soft 版本号  ： 只重置仓库区
​		git reset --mixed 版本号 ： 重置仓库区和暂存区【默认】
​		git reset --hard  版本号 ： 重置仓库区和暂存区和工作区。
​		git reset 版本号         : 效果与--mixed一致

### git 分支

#### 	创建分支  

​		git branch  分支名称

#### 	查看分支

​		git branch

#### 	切换分支

​		git checkout  分支名称

#### 	创建并切换分支

​		git checkout -b  分支名称

#### 	删除分支

​		git branch -d 分支名称
​			注意：不能在当前分支删除当前分支，需要切换到其他分支才能删除。
​			注意：master分支是可以删除的，但是不推荐那么做。

#### 	合并分支

​		git merge  分支名称
​			例如: 在master分支中执行git merge dev 将dev分支中的代码合并到master分支
​	合并冲突
​		对于同一个文件，如果有多个分支需要合并时，容易出现冲突。
​		合并分支时，如果出现冲突，只能手动处理，再次提交，一般的作法，把自己的代码放到冲突代码的后面即可。

### git clone   拉去远程仓库地址

​                  git clone 远程仓库地址  文件夹名字

###  git push   向远程仓库提交代码                

​		git push 远程仓库地址   分支名

### 其他

git pull 拉取更新

  git  remote  	查看所有的仓库变量

git  remote   add 变量名   仓库地址    添加别名

git  remote   remove  变量名  移除别名                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          