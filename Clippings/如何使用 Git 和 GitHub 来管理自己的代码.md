---
title: "如何使用 Git 和 GitHub 来管理自己的代码"
source: "https://mp.weixin.qq.com/s/58zIkG2W9dwuYrnSX4nwsw"
author:
  - "[[娄伯狄]]"
published:
created: 2025-03-16
description: "git \x26amp; github"
tags:
  - "clippings"
---
原创 SongBot视觉实验室

![profile_qrcode](https://mp.weixin.qq.com/mp/qrcode?scene=10000005&size=102&__biz=MzIxNDU3Njk5NQ==&mid=2247486244&idx=1&sn=f695bc8f3ff9a046f41c2d77f76d5ed6&send_time=)

SongBot视觉实验室

主流工业机器人和机器视觉的各类应用编程技术介绍，以及技术支持和技术培训服务

155篇原创内容

*2022年03月24日 07:18*

**1.配置git环境**  

1）点击 "Git Bash" 打开 Git 命令控制台

![图片](https://mmbiz.qpic.cn/mmbiz/xnMLeA8ESjsJMaEYZy4trTYRMgdvNLz2fic0k5Ut7IPfkfRiayOLFUWTEMVKK1Kg7UQhlBasB6SmomwVxW3ibBXxQ/640?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

2）生成秘钥文件来连接 GitHub，在控制台输入如下指令并连续敲 3 次回车即可

```shell
$ ssh-keygen -t rsa -C "myMailbox@163.com"
```

    备注："myMailbox@163.com" 是你的邮箱地址，需要注意的是 "ssh-keygen" 之间是没有空格的，其他的之间是有空格的。

![图片](https://mmbiz.qpic.cn/mmbiz/xnMLeA8ESjsJMaEYZy4trTYRMgdvNLz2Xk4yaZJjnQblYeyzYhItrEe44gDzZSgjP2EM8hMUIudFwFqLAmv0fQ/640?wx_fmt=other&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

3）秘钥生成后可以在 "C:\\Users\\Administrator\\.ssh" 文件夹下找到秘钥文件 "id\_rsa.pub"

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

4）在登录的 GitHub 账户中配置 "SSH keys"，点击用户头像指示的三角图标选择 "Settings"，然后选择 "SSH and GPG keys"，点击右侧 "SSH keys" 栏中的 "New SSH key" 按钮进行配置（其中 Title 可以自己随意起一个名字，而 Key 的内容就是将 "id\_rsa.pub" 文件中的内容全部复制过来即可），点击 "Add SSH key" 按钮完成操作，此时在你填写的邮箱中会收到一封确认的邮件可以不用管它。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)  

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

5）验证 Git 环境是否配置成功

```ruby
 $ ssh -T git@github.com
```

备注：

1. 当提示输入（yes/no）? 时，在后面输入 yes 回车即可，如果看到欢迎语 "Hi xxx! You've successfully authenticated, but GitHub does not provide shell access" 则表示配置成功。

2\. 如果提示类似 "ssh: Could not resolve hostname \\342\\200\\223t: Name or service not known" 的错误，解决办法是执行命令：ssh -t -p 22 git@github.com（其中 -p 表示修改服务器端口为22）。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

**2.创建本地仓库**  

1）选中创建的仓库目录右击鼠标，在弹出的菜单中选择 "Git Bash Here" 选项后就会在此目录中打开我们的 Git 命令控制台，进入到了本地仓库的根目录下。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

2）初始化 Git 仓库，操作完成后会在此目录中生成一个隐藏的 .git 后缀文件

```shell
 $ git init
```

备注：初始化必须进入到本地仓库的根目录下面。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

3）添加远程仓库管理

```ruby
$ git remote add origin git@github.com:userName/hello-word.git
```

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

    备注：

   其中 "git@github.com:userName/hello-word.git" 是我们 GitHub 中 "hello-word" 项目的 ssh 地址，"userName" 是我们在 GitHub 网站上注册时使用的用户名，"hello-word.git" 是我们为这个项目建立的仓库名。

4）如果在 GitHub 上创建仓库的时候将 "README" 选项选择了则就已经算是一次提交了，若需要在本地同步远程仓库的内容则使用如下命令即可

```ruby
 $ git pull git@github.com:userName/hello-word.git
```

 或者

```shell
 $ git pull origin master
```

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

备注："userName" 是我们 GitHub 账号的用户名，"hello-word.git" 是我们为这个项目建立的仓库名，执行如上命令成功后在将会在本地仓库的根目录下生成从远程仓库同步下来的 "README.md" 文件。

  
![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

**3.在本地仓库上传代码到远程仓库** 

1）将需要上传的文件放入本地仓库的根目录中

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

2）添加当前更改或新增文件到本地 Git 仓库中

    1> 添加指定文件

```shell
$ git add hello-word.txt
```

    备注：添加当前目录中的 "hello-word.txt" 文件到本地 Git 仓库中。

    2\> 添加全部文件

```cs
git add .
```

    备注："add" 后面加点意思就是将本仓库中的所有内容添加到本地仓库中。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

3）提交当前工作空间的修改内容

```shell
 $ git commit -m "XXX"
```

        
 备注：

"XXX" 是提示信息，此

提示信息是一定要写的，不仅是规则同时也方便我们记录此次操作的是什么内容。

4）推送本地仓库内容到远程仓库

```perl
$ git push git@github.com:userName/hello-word.git
```

    或者 

```shell
$ git push -u origin master
```

    备注："userName" 是我们 GitHub 账号的用户名，"hello-word.git" 是我们为这个项目建立的仓库名。

![图片](https://mp.weixin.qq.com/s/www.w3.org/2000/svg'%20xmlns:xlink='http://www.w3.org/1999/xlink'%3E%3Ctitle%3E%3C/title%3E%3Cg%20stroke='none'%20stroke-width='1'%20fill='none'%20fill-rule='evenodd'%20fill-opacity='0'%3E%3Cg%20transform='translate(-249.000000,%20-126.000000)'%20fill='%23FFFFFF'%3E%3Crect%20x='249'%20y='126'%20width='1'%20height='1'%3E%3C/rect%3E%3C/g%3E%3C/g%3E%3C/svg%3E)

5）如果出现 "non-fast-forward" 错误，主要是因为 GitHub 仓库中已经存在有一部分内容了，所以它不允许你直接把你的内容覆盖上去，比如有的人在新建仓库配置信息时将 "README" 文件选项打钩了可能就会出现这种情况，此时可以使用如下方法解决

```shell
 $ git push --all -f
```

备注：强推即利用覆盖方式将你本地的代码替代 GitHub 仓库内的内容  

6\. 至此上传文件就结束了，你可以到你的 GitHub 项目主页（https://github.com/userName/hello-word.git） 看到从本地仓库上传到 GitHub 远程仓库的文件了。

  
PS：copy by https://www.jianshu.com/p/7fa6b2d81f19