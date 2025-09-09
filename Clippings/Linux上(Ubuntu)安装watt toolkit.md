---
title: "Linux上(Ubuntu)安装watt toolkit"
source: "https://zhuanlan.zhihu.com/p/707174795"
author:
  - "[[要不要太吊]]"
published:
created: 2025-09-08
description: "记录在新安装的ubuntu中安装watt toolkit工具箱的过程。 1、打开Watt Toolkit官网，点击下载按钮，弹出linux下脚本安装方法弹窗；2、在命令行终端输入命令curl -sSL https://steampp.net/Install/Linux.sh | bash…"
tags:
  - "clippings"
---
![Linux上(Ubuntu)安装watt toolkit](https://pic1.zhimg.com/70/v2-596f4f165428e2b5c68c031420593358_1440w.avis?source=172ae18b&biz_tag=Post)

Linux上(Ubuntu)安装watt toolkit

目录

收起

1、打开Watt Toolkit官网，点击下载按钮，弹出linux下脚本安装方法弹窗；

2、在命令行终端输入命令

3、重新执行上一个命令，报警告

4、查询字符集，发现没有en\_US.UTF-8

5、再次执行安装命令，成功

6、打开watt toolkit软件，选择一键加速，弹出网页，显示缺少证书

7、按上面网页提示，在浏览器导入证书

8、完成后，再次尝试开启watt toolkit一键加速，再次弹出网页，显示没有hosts文件修改权限

9、按照提示，在命令行执行命令

10、再次尝试开启加速

![](https://pic2.zhimg.com/v2-a7eb65a20d809ef424b073e4bfb5c053_1440w.jpg)

记录在新安装的ubuntu中安装 watt toolkit 工具箱的过程。 1、打开Watt Toolkit官网，点击下载按钮，弹出linux下脚本安装方法弹窗； 2、在命令行终端输入命令 curl -sSL https://steampp.net/Install/Linux.sh | bash 显示找不到curl命令 安装curl sudo apt install curl 3、重新执行上一个命令，报警告 ~$ curl -sSL https://steampp.net/Install/Linux.sh | bash bash: 行 32: 警告： setlocale: LC\_ALL: 无法改变区域设置 (en\_US.UTF-8)：没有那个文件或目录 证书导入以及验证需要使用 certutil 工具。 4、查询字符集，发现没有en\_US.UTF-8 locale -a // C C.utf8 POSIX zh\_CN.utf8 zh\_SG.utf8 执行下面命令，生成 en\_US.UTF-8这个字符集的locale文件 sudo localedef -i en\_US -f UTF-8 en\_US.UTF-8 重新查询，就有了en\_US.utf8字符集 locale -a // C C.utf8 en\_US.utf8 POSIX zh\_CN.utf8 zh\_SG.utf8 5、再次执行安装命令，成功 ~$ curl -sSL https://steampp.net/Install/Linux.sh | bash certutil 工具已安装。 zenity 工具已安装。 jq 工具已安装。... 6、打开watt toolkit软件，选择一键加速，弹出网页，显示缺少证书 7、按上面网页提示，在浏览器导入证书 点击导入按钮，选择steem++的证书： 8、完成后，再次尝试开启watt toolkit一键加速，再次弹出网页，显示没有hosts文件修改权限 9、按照提示，在命令行执行命令 sudo chmod a+w /etc/hosts 10、再次尝试开启加速 成功！

发布于 2024-07-05 01:14・上海[Ubuntu](https://www.zhihu.com/topic/19557067)[Linux](https://www.zhihu.com/topic/19554300)

写下你的评论...

还没有评论，发表第一个评论吧

![](https://static.zhihu.com/heifetz/assets/liukanshan-peek.a71ecf3e.png) 登录即可查看 超5亿 专业优质内容

超 5 千万创作者的优质提问、专业回答、深度文章和精彩视频尽在知乎。

![](https://static.zhihu.com/heifetz/assets/liukanshan-peek.a71ecf3e.png) 登录即可查看 超5亿 专业优质内容

超 5 千万创作者的优质提问、专业回答、深度文章和精彩视频尽在知乎。