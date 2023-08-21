# 第1章 Git概述

## 1 Git工作机制

![1689925295527](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689925295527.png)

工作区就是自己写代码的位置，暂存区临时存储，这两部分都不会生成历史版本，但是提交到本地库之后就会生成对应的历史版本了。

## 2 Git和代码托管中心

代码托管中心是基于网络服务器的远程代码仓库，一般我们简单称为远程库。

1. 局域网

   GitLab

2. 互联网

   **GitHub**

   Gitee码云



# 第2章 Git安装

官网下载 https://git-scm.com/ 全部默认即可

如何查看安装成功：右键git bash，能打开这个页面就是ok的

![1689926099597](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689926099597.png )



# 第3章 Git常用命令

## 1. 设置用户签名

```bash
 给i
```

这个用户名和邮箱是可以随便设置的，与之后的登录的无关。

## 2.  初始化本地库

让git获得目录的**管理权**，方面git管理目录，可以使用下面的指令：

```bash
git init
```

初始化授权完成之后，就会出现一个master

![1689927584406](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689927584406.png)

也可以使用下面的命令查看本地库状态：

```bash
git status
```

![1689927711402](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689927711402.png)

新建一个hello.txt，再次运行git status，就会发生变化：

![1689928506718](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689928506718.png)

## 3.  添加暂存区

```bash
git add 文件名
```

再使用git status，就会发现：

![1689928833418](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689928833418.png)

红色变成了绿色，说明文件已经放到了暂存区。

如果需要删除暂存区的文件（注意，此时工作区还是存在该文件的），可以使用下面的指令：

```bash
git rm --cached 文件名
```

## 4.  提交本地库

```bash
git commit -m "日志信息" 文件名
```

![1689929332941](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689929332941.png)

此时再运行git status，如下所示：

![1689930661879](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689930661879.png)

上面就表示提交本地库成功了

查看提交版本日志：

```bash
git reflog
```

![1689931909992](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689931909992.png)

查看详细日志

```bash
git log
```

![1689931943925](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689931943925.png)

## 5. 修改文件

将hello.txt修改一下，然后查看状态：

![1689932065069](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689932065069.png)

变红了，说明这次文件的修改没有添加到暂存区，使用git add hello.txt

![1689932220002](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689932220002.png)

提交：

```bash
git commit -m "second commit" hello.txt
```

查看日志：

![1689932275693](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689932275693.png)

## 6. 版本穿梭

可以使用reflog以及log查看项目的提交日志。

```bash
git reset --hard 版本号前6位
```

# 第4章 Git的分支操作

 ![1689942459415](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689942459415.png)

**分支的好处**：同时并行推进多个功能开发，提高开发效率。各个分支在开发过程中，如果某一个分支开发失败，不会对其他分支有任何影响。失败的分支删除重新开始即可。

## 1. 查看分支

```bash
git branch -v
```

## 2. 创建分支

```bash
git branch 分支名
```

![1689942816859](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689942816859.png)

## 3. 修改分支 & 切换分支

```bash
git checkout 分支名
```

然后查看分支：git branch -v

![1689943062948](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689943062948.png)

注意：**切换分支之前，确保已经对当前分支做出的修改进行了commit**，否则别的分支也会改



## 4. 分支合并

```bash
git merge 需要合并的分支
```

**在哪个分支上执行这个命令，最终就是哪个分支被改变**。（有点儿强行覆盖的感觉）

**冲突合并：**

​        合并分支时，两个分支在**同一个文件的同一个位置**有两套完全不同的修改。Git无法替我们决定使用哪一个。必须**人为决定**新代码内容。

![1689947192898](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689947192898.png)****

注意，合并冲突的前提是两个代码的版本之前必须一样，然后分别做修改，然后合并的时候会发生冲突。发生冲突的时候，会显示MERGING，此时需要人为修改。

注意：修改完之后，需要add到暂存区，**commit提交的时候不能有文件名字**。( 上面已经给出了示例)

# 第5章 Git团队协作机制

使用代码托管中心发到远程库。

团队内协作和跨团队协作参看这个视频：

[19_尚硅谷_Git_团队协作_团队内协作和跨团队协作_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1vy4y1s7k6?p=19&spm_id_from=pageDriver&vd_source=1f0bb31242a54232ecf6ae0ca2dc8304)

# 第6章 GitHub操作

创建远程仓库，仓库名和本地的名字尽量保持一致

## 1. 创建远程库别名

查看远程库别名：

```bash
git remote -v
```

创建别名：最好和库名保持一致

```bash
git remote add 别名 链接
```

创建成功之后查看就有两个：表示**既可以推送也可以拉取**

![1689988840619](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689988840619.png)

## 2. 推送本地分支到远程仓库

```bash
git push 别名(链接) 分支
```

如果出现**time-out**的错误，要科学上网；

如果出现**Couldn‘t connect to server**，参考[(42条消息) [报错解决\] Failed to connect to github.com port 443 after ***** ms: Couldn‘t connect to server_一件迷途小书童的博客-CSDN博客](https://blog.csdn.net/m0_64007201/article/details/129628363)。

```bash
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy http://127.0.0.1:7890
```

然后登录即可

## 3. 拉取远程库到本地库

```bash
 git pull 别名 分支
```

## 4. 克隆远程仓库到本地

克隆代码不需要登录账号，也不需要初始化本地库

```bash
git clone 仓库地址
```

clone会做如下操作：1、拉取代码；2、初始化本地库；3、创建别名（别名默认为origin）

## 5. 团队内协作

项目成员更改代码之后，可以使用push将代码推送到远程仓库，前提是仓库的管理者需要给项目成员权限（**邀请**），邀请的流程如下：

[(42条消息) GitHub项目邀请（添加）成员_github看不到邀请_逸然逸生的博客-CSDN博客](https://blog.csdn.net/qq_38502736/article/details/107216862)

https://blog.csdn.net/qq_38502736/article/details/107216862

然后就可以正常的push和pull了。

## 6. 跨团队协作

别的团队的开发者可以使用**fork**将地址的内容搞到自己的远程仓库，这里介绍了fork和clone的区别

[Git 在GitHub中，Fork和Clone的区别是什么|极客笔记 (deepinout.com)](https://deepinout.com/git/git-questions/1214_git_what_is_the_difference_between_forking_and_cloning_on_github.html#:~:text=Fork和Clone是Git中常用的操作，用于将远程仓库克隆到本地。 Fork是GitHub特有的操作，用于在GitHub上创建一个原项目的独立副本。 区别总结如下：,– Fork是在GitHub上创建一个独立的仓库，而Clone是将远程仓库的内容完整克隆到本地。 – Fork后的仓库与原项目之间是完全独立的，没有直接联系，而Clone仓库是远程仓库的一个镜像。)

别的团队开发好之后，选择**Pull requests**，然后**New pull request**

![1689995040882](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\1689995040882.png)

如果没问题的话，就点击**Merge pull request**

## 7. ssh免密登录

在c盘用户文件夹下，git bash生成.ssh文件

```bash
ssh-keygen -t rsa -c github邮箱
```

然后找到公钥，添加到github的setting中即可，详细的步骤如下：

[(42条消息) github的免密码登录（ssh key）_github key 登录_是大侠诶的博客-CSDN博客](https://blog.csdn.net/qq_41563601/article/details/105467023)

[26_尚硅谷_Git_GitHub_SSH免密登录_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1vy4y1s7k6?p=26&vd_source=1f0bb31242a54232ecf6ae0ca2dc8304)

设置好之后就可以使用ssh了，就不用每次都输入密码了。

这里面linux系统下的也讲了

# 第7章 IDE集成github（待完善）



# 第8章 国内托管中心-码云

创建操作基本上跟GitHub是一致的

## 1. 码云导入Github项目

导入已有仓库，直接输入链接即可。

# 第9章 自建代码托管平台-GitLab

## 1. GitLab官网地址

官网地址：[The DevSecOps Platform | GitLab](https://about.gitlab.com/)

这里暂时不看



# 如何提交整个文件夹

在git add的时候执行下面的命令即可

```bash
git add .
```

撤销init，或者说是删除本地库，使用：

```bash
rm -rf .git
```





