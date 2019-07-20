# gitdemo
git使用教程
---------------------------1------------------------------ 

git

什么是仓库？

版本库仓库：存储代码文件的地方

本地仓库：本机仓库

远程仓库：充当中央服务器，用于不同的节点之间进行代码交换的地方

克隆：复制

分支 不同的分支做不同的事，用于协同

标签 用于标注版本信息的指针，指向一个commit位置

--------------------------------------------------------------------

-------------------------------2--------------------------------- 
git常用命令
远程仓库存储位置
--github
--gitlab
--coding
--gitee

安装git
sudo apt-get install git
git --version (查看git版本)
tarena@tedu:~/mongodb/student$ git --version
git version 2.7.4

使用git
1 新建空目录用于创建仓库
mkdir gitdemo

2 打开空目录里
cd gitdemo

3 使用git初始化仓库，将空目录变为空仓库
git init

4 查看空仓库
ls -a

5 创建文件/代码文件
touch abc.txt

6 使用git将文件加到仓库中，并未入库
git add abc.txt
*****没有任何提示表示没有问题*****

7 使用git将文件提交到仓库中
git commit -m "xxxxxx"
eg.git commit -m "add abc.txt"
**** -m "注释内容"****

8 上述命令报错
@tedu:~/gitdemo$ git config --global user.email "xxxxxxxx@qq.com"
@tedu:~/gitdemo$ git config --global user.name "xxxxxxxx"

9 查看当前仓库的状态
git status

10 查看修改文件的修改内容
git diff abc.txt 

通过查看日志文件，获取提交记录
git log

回退到之前版本（根据git log的日志内容进行回退）
git reset --hard HEAD^    （往前退几步‘^’符号就有几个）
git reset --hard [commit_id]
(注：commit_id只需要写前7位就可以了)
git log内容
commit 34a3f2cebb7f9dcd54573972581fdf7a25c47258
（只能回退 add到仓库并且commit提交了的代码）

删除仓库中文件
git rm def.txt
git rm --cached [文件/目录]

--------------------------------3----------------------------------- 
远程仓库和本地仓库建立链接
远程仓库github （svn的中央服务器是东西最全的，github所有服务器都是平等的）
进入自己的账号首页
创建第一个项目

远程仓库coding
注册账号
进入自己的账号首页
创建第一个项目

git pull origin master

先有本地仓库，后有远程仓库(远程仓库和本地仓库是不同节点上的仓库)
获取远程仓库，与本地仓库之间建立链接关系
git remote add origin https://github.com/xiaobh2010/gitdemo.git     （https的地址）

------------------------4------------------------------------- 
使用SSH进行上传提交更新时需要公钥生成获取pubkey
ssh-keygen -t rsa -b 4096 -C "youremail"
生成的pubkey默认位置/home/tarena/.ssh/目录下
打开id_rsa.pub 复制内容
在github中settings中SSH and GPG key中添加SSH key
添加内容为上述的复制内容
（报错 sign_and_send_pubkey:...
  解决方法：运行ssh-add）

从远程仓库同步到本地仓库
git pull origin master    origin是主机名称    master是分支名称

从本地仓库推送到远程仓库
git push origin master

git add xxx
git commit -m "xxxx"    分号里面是注释内容可以随意添加
（添加的文件需要提交到本地仓库才能推送到远程仓库）

-----------------------------------5----------------------------------------
克隆和分支
先创建远程仓库，再有本地仓库
克隆远程仓库到本地空目录下
git clone https://github.com/xiaobh2010/gitdemo.git
自动生成对应的本地仓库，本地仓库与远程仓库相对应

分支：不同分支做不同的事，用于协同
（标签指向分支，分支就成了主干）
1 创建分支
git branch 分支名称
git branch 查看分支
    列出分支，并标注出当前所处分支
tarena@tedu:~/gitdemo$ git branch dev
tarena@tedu:~/gitdemo$ git branch      （两个分支，现在处于master分支）
  dev
* master        

2 切换分支
分支查看
git branch -a
* 表示正在哪个分支上工作

git checkout 分支名称
提示出已经切换到xxx分支

git checkout -b abc
创建新分支并切换到新分支之上

3 合并分支，将其他分支合并到当前分支
    git merge 其他分支名称
示例：
将分支abc合并到当前的分支
git merge abc

4 删除分支，删除不需要的分支
git branch -d 要删除的分支名称
git branch -d dev

从远程仓库获取代码到本地，发现代码报错，通过创建分支来保存自己将要上传的代码，
从而不对原代码产生影响

-------------------------------------6-----------------------------------------
标签
用于标注版本信息的指针，指向某一个commit的位置

创建标签
git tag v1.0
查看标签
git tag 
查看标签
git show 标签名
日志信息在一行显示
git log --oneline
tarena@tedu:~/gitdemo$ git log --oneline
3a28d21 tag2
b26f5ac tag1
a7d7fe7 tag1
05c4e61 tag1
fb4ea7d tag
对上述的信息打标签
git tag -a v1.5 -m "set tag" fb4ea7d
git tag
可以查看当前所有的标签，看到已经添加进去了

git show v1.5 
就可以查看当前标签指向的commit内容了

对已操作过的commit进行添加标签
git tag -a 标签名称 -m “标签注释” commit的id

返回之前的某个版本
git reset --hard 版本号
（ssh通过ssh获取仓库，需要在github上生成私钥）

标签应该在对文件进行了修改，添加和提交之后加上，再使用git show v版本号就能看到修改信息

标签查看
git tag

添加标签
git tag [t_name] [commit_id] -m '注释内容'
git tag可以查看标签

查看标签的详细信息
git show [tag] 

给之前版本打标签
git tag v0.9 5a57ab5 -m 'add tag' （根据git log中记录的commit_id来打标签）

删除标签
git tag -d v0.9

查看详细标签信息
git show [tag]

标签跳转
git reset --hard [tag]

删除标签
git tag -d [tag]

5 保存工作区
工作区保存（对文件进行修改）
查看保存的工作区
git stash list

保存工作区
git stash save [message]

应用工作区
git stash apply stash@{n}  

删除工作区
git stash drop stash@{n}  （删除指定工作区）
git stash clear (删除所有工作区)

eg:
tarena@tedu:~/20190714/git$ git stash list
tarena@tedu:~/20190714/git$ l
exec.py  README.md  test/
tarena@tedu:~/20190714/git$ vi exec.py 
tarena@tedu:~/20190714/git$ git stash save 'one'
Saved working directory and index state On master: one
HEAD 现在位于 2e4c044 mv file
tarena@tedu:~/20190714/git$ git stash list
stash@{0}: On master: one
tarena@tedu:~/20190714/git$ vi exec.py 
tarena@tedu:~/20190714/git$ git stash save 'two'
Saved working directory and index state On master: two
HEAD 现在位于 2e4c044 mv file
tarena@tedu:~/20190714/git$ git stash list
stash@{0}: On master: two
stash@{1}: On master: one
tarena@tedu:~/20190714/git$ git stash apply stash@{1}
位于分支 master
尚未暂存以备提交的变更：
  （使用 "git add <文件>..." 更新要提交的内容）
  （使用 "git checkout -- <文件>..." 丢弃工作区的改动）

	修改：     exec.py

修改尚未加入提交（使用 "git add" 和/或 "git commit -a"）
tarena@tedu:~/20190714/git$ git add *
tarena@tedu:~/20190714/git$ l
exec.py  README.md  test/
tarena@tedu:~/20190714/git$ git commit -m 'stash add'
[master 9bde97a] stash add
 1 file changed, 1 insertion(+)












