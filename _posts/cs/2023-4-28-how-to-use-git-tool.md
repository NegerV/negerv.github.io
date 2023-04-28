---
title: Git使用方法
key: how-to-use-git-tool
tags: "Git"
modify_date: "2023-04-28 22:00:00"
article_header:
aside:
    toc: true
---

## 初次上传本地库



在github创建仓库后，在本地文件夹使用`git clone`指令将远程仓库clone到本地。

首先打开git bash，cd到项目下

```
git clone xxxx.git // 确保一致
git init   // 初始化版本库
git add .   // 添加文件到版本库（只是添加到缓存区）,"."代表添加文件夹下所有文件 
git commit -m "first commit" // 把添加的文件提交到版本库，并填写提交备注(备注随意)
```

到目前为止，我们完成了代码库的初始化，但代码还在本地，并未提交到远程目标服务器，为提交到远程代码服务器，进行以下两步：

```
git remote add origin 你的远程库地址  // 把本地库与远程库关联
git push -u origin master    // 第一次推送时,这里要注意自己的库到底是master还是main
git push origin master  // 第一次推送后，直接使用该命令即可推送修改
```

​		把本地库的内容推送到远程。使用`git push`命令，实际上是把当前分支master推送到远程。执行此命令后会要求输入用户名、密码。验证通过后即开始上传。
​		说明：用户名密码需要通过命令 `ssh-keygen -t rsa -C 邮箱地址`进行创建，并且要把得到的RSA秘钥（公钥）文件放到git服务器上，这样才有权限进行代码推送



## git提交代码



先进入到项目根目录下：

	cd D:\hanchuang

查看是否有冲突：

	git status

将当前工作目录中更改或者新增的文件加入到Git的索引中，加入到Git的索引中就表示记入了版本历史中

	git add .

添加注释（必填）：

	git commit -m "注释内容"

**如果发生冲突**（这一点很重要），拉一下远端的仓：使用`git pull origin master`，拉一下远端的仓代码，然后弹出的文件，q! 退出即可

	git pull origin master xxxxxx.git

提交本次修改到远程仓库

	git push -u origin master // -u代表强制执行



## git删除远程文件



本地云端一起删除

    git rm 文件 // 更新后，本地该文件会被删除
    git rm -r 文件夹 // 删除文件夹
    git commit -m '删除某个文件'
    git push origin master

只删除云端

    git rm --cached 文件 //本地中该文件不会被删除
    git rm -r  --cached  文件夹 //删除文件夹



## 解决git 10054错误



使用git获取github上代码时报错：`OpenSSL SSL_read: Connection was reset, errno 10054`

但此时又必须开着梯子才能访问到github

	修改设置，解除ssl验证：git config --global http.sslVerify "false"

此时，再执行git操作即可。

注：设置后关闭当前git窗口，重新打开再执行git操作

