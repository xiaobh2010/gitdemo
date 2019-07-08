# gitdemo
git使用教程



1 git

什么是仓库？

版本库仓库：存储代码文件的地方

本地仓库：本机仓库

远程仓库：充当中央服务器，用于不同的节点之间进行代码交换的地方

克隆：复制

分支

标签

--------------------------------------------------------------------

2 git常用命令
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
@tedu:~/gitdemo$ git config --global user.email "545756210@qq.com"
@tedu:~/gitdemo$ git config --global user.name "xiaobohan"

9 查看当前仓库的状态
git status

10 查看修改文件的修改内容
git diff abc.txt 


通过查看日志文件，获取提交记录
git log

回退到上一个版本
git reset --head HEAD
（只能回退 add到仓库并且commit提交了的代码）

删除仓库中文件
git rm def.txt


3 远程仓库和本地仓库建立链接
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






