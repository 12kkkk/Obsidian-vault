---
title: "如何在GitHub分享自己的代码（附上传大文件步骤）"
source: "https://blog.csdn.net/weixin_51570804/article/details/137178933"
author:
  - "[[weixin_51570804]]"
published: 2024-03-31
created: 2025-08-30
description: "文章浏览阅读8.7k次，点赞61次，收藏128次。本文详细介绍了如何在GitHub上创建远程仓库，安装Git，配置邮箱和用户名，上传代码，以及处理大文件的GitLargeFileStorage(GitLFS)流程。步骤包括初始化本地仓库、添加文件、提交和推送代码，以及注意事项和特殊情况处理。"
tags:
  - "clippings"
---
本文详细介绍了如何在GitHub上创建远程仓库，安装Git，配置邮箱和用户名，上传代码，以及处理大文件的GitLargeFileStorage(GitLFS)流程。步骤包括初始化本地仓库、添加文件、提交和推送代码，以及注意事项和特殊情况处理。

摘要生成于 [C知道](https://ai.csdn.net/?utm_source=cknow_pc_ai_abstract) ，由 DeepSeek-R1 满血版支持， [前往体验 >](https://ai.csdn.net/?utm_source=cknow_pc_ai_abstract)

最近应老师要求，需要上传一些代码到GitHub上，以前只下载过别人的项目，还没上传过自己的项目，于是在网上搜索学习了一下，成功上传了自己的项目，结合了几个教程，总结了下面的步骤，大家可以参考一下。

参考的一些文章和视频：

[github大文件提交以及LFS的简单使用 - 简书 (jianshu.com) https://www.jianshu.com/p/22e9eb221fd4](https://www.jianshu.com/p/22e9eb221fd4 "github大文件提交以及LFS的简单使用 - 简书 (jianshu.com)") [手把手教你在github上传文件\_哔哩哔哩\_bilibili https://www.bilibili.com/video/BV1Xs4y1i7id/?spm\_id\_from=333.337.search-card.all.click&vd\_source=7a0d8721998d1825b5e8304262c30c8e](https://www.bilibili.com/video/BV1Xs4y1i7id/?spm_id_from=333.337.search-card.all.click&vd_source=7a0d8721998d1825b5e8304262c30c8e "手把手教你在github上传文件_哔哩哔哩_bilibili")

## 第一步：创建自己的远程仓库。

![](https://i-blog.csdnimg.cn/blog_migrate/760d8f5dde90e666f84411b7f81bda08.png)

![](https://i-blog.csdnimg.cn/blog_migrate/fca344b98ec846c8dcf9eb6b9c0f2135.png)

![](https://i-blog.csdnimg.cn/blog_migrate/f3466c644b361830d9de723cee7e5680.png)

创建好的仓库如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/f824578ebf2ca6ecd6fcd9ef35d2f583.png)

## 第二步：下载并安装Git软件

参考网址 [Git - Downloads (git-scm.com)](https://git-scm.com/download "Git - Downloads (git-scm.com)") ，下载对应版本，以我的电脑为例，下载64位 Windows 版本。如下图：

![](https://i-blog.csdnimg.cn/blog_migrate/9da8c193c061d289811b759d1357552b.png)

安装Git，除了安装路径我自己重新设置了，其余我都选择了默认选项，如需要Git安装过程中的详细释义，见： [Git 详细安装教程（详解 Git 安装过程的每一个步骤）\_git安装-CSDN博客 https://blog.csdn.net/mukes/article/details/115693833](https://blog.csdn.net/mukes/article/details/115693833 "Git 详细安装教程（详解 Git 安装过程的每一个步骤）_git安装-CSDN博客")

## 第三步：上传代码。

### 一般的步骤：

①在需要上传的文件夹（称为本地仓库）目录下右键'Open Git Bash here'：

![](https://i-blog.csdnimg.cn/blog_migrate/9900a597c63b2e439117b6ba2326a8f0.png)

②在命令行输入下面一行命令以初始化：

```bash
git initbash
```

![](https://i-blog.csdnimg.cn/blog_migrate/ea193229b856fd23b59580cab6006101.png)

点击“隐藏的项目”即可看到'git'文件，如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/5c560436199234cd02815c3bddefafdb.png)

③在命令行输入下面一行命令，将当前工作目录下未被Git管理的文件和修改过的文件添加到暂存区中，准备提交到库（ 注意：如果上传的文件中有超过50M的大文件，需要将大文件和小文件分开提交，不要跟着接下来的步骤做了，转到步骤⑪ ）：

```bash
git add *bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/3b53183377574913d798a520bffe692f.png)

④右键记事本打开'.git'文件夹下的'config'文件：

![](https://i-blog.csdnimg.cn/blog_migrate/4d58d3494e3052e6cb84520d9b2c5968.png)

⑤在代码最后加上自己 [GitHub账号](https://so.csdn.net/so/search?q=GitHub%E8%B4%A6%E5%8F%B7&spm=1001.2101.3001.7020) 的邮箱和用户名并保存，添加的代码如下（ 千万不要手误把自己的用户名和邮箱打错了，我就吃过这个亏 ）：

```bash
[user]

email = GitHub账号的邮箱

name = GitHub账号的用户名
bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/277bf630f7fe38779cdc4bd97a657cca.png)

⑥ 在命令行输入下面一行命令，将暂存区中的改动提交到仓库。

> 其中“first commit”是一条提交信息（Commit Message），用于描述这次提交的内容或目的。通常，项目的第一次提交被称为 "Initial Commit" 或 "First Commit"，它标志着项目的初始状态，包括了项目的基本文件结构、配置文件或初始代码。

```bash
git commit -m "first commit"bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/8be64a806f61efafc8315358bbaf82cf.png)

⑦在GitHub远程仓库下复制链接：

![](https://i-blog.csdnimg.cn/blog_migrate/ab5cc4118f08c8294fdfd4424824c58d.png)

⑧在命令行输入下面一行命令，将本地仓库与远程仓库关联起来（右键粘贴复制的链接可能会引起后面格式错误，所以我往往会自己敲进去）：

```bash
git remote add origin 右键粘贴远程仓库链接bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/56f432ce6b09423800f9032002c3293a.png)

⑩在命令行输入下面一行命令，将本地仓库提交上传到远程仓库：

> 这条命令的作用是将当前分支（master）的提交推送到名为（origin）的远程仓库。其中 -u 参数用于设置上游（upstream）分支，这样在以后的推送或拉取操作中，Git就会知道应该将本地的master分支与远程的origin/master分支进行同步。
> 
> 执行这条命令后，如果远程仓库中还没有master分支，Git 会创建一个新的master分支，并将你的提交推送到该分支。如果远程仓库中已经存在master分支，Git 将会将你的提交合并到远程master分支上。

```bash
git push -u origin masterbash
```

![](https://i-blog.csdnimg.cn/blog_migrate/84290145d08e246e6f74efbf2496022f.png)

不出意外的话，代码应该顺利上传，如下图：

![](https://i-blog.csdnimg.cn/blog_migrate/01591b19c62ef160d970c4181992a828.png)

如果前面步骤都无误的情况下最后一步上传本地仓库报错，大概率是网络连接问题导致与GitHub连接中断，要么多试几次，要么使用代理，使用代理的方法可见： [提交代码到github时使用代理\_github 代理-CSDN博客 https://blog.csdn.net/Xzike/article/details/131661141](https://blog.csdn.net/Xzike/article/details/131661141 "提交代码到github时使用代理_github 代理-CSDN博客") 以上就是上传仓库的整个步骤了。

### 下面是特殊情况，存在大文件时的上传步骤：

前面的步骤①和②是一样的，接下来：

⑪ 安装Git LFS，在下面官网上下载安装即可。 [Git Large File Storage | Git Large File Storage (LFS) replaces large files such as audio samples, videos, datasets, and graphics with text pointers inside Git, while storing the file contents on a remote server like GitHub.com or GitHub Enterprise. (git-lfs.com) https://git-lfs.com/](https://git-lfs.com/ "Git Large File Storage | Git Large File Storage (LFS) replaces large files such as audio samples, videos, datasets, and graphics with text pointers inside Git, while storing the file contents on a remote server like GitHub.com or GitHub Enterprise. (git-lfs.com)")

![](https://i-blog.csdnimg.cn/blog_migrate/4098279e14c1532a918ab3389b683d4a.png)

⑫ 在命令行输入下列一行命令。

```bash
git lfs installbash
```

![](https://i-blog.csdnimg.cn/blog_migrate/b81d07ed2643f01f87a46cc2434cc0e3.png)

⑬在命令行输入下列命令以跟踪大文件。

```bash
git lfs track "xxx.xx"bash
```

以我的文件为例，如下图：

![](https://i-blog.csdnimg.cn/blog_migrate/20dda08e12f243005d5322562768d678.png)

⑭ 输入下面一行命令将'.gitattributes'文件添加到Git中：

```bash
git add .gitattributesbash
```

![](https://i-blog.csdnimg.cn/blog_migrate/81cdb80fa24b9e36f191f3a501e091c1.png)

⑮输入下面一行命令提交'.gitattributes'文件：

```bash
git commit -m "add file .gitattributes"bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/52ed2fc59931e04e75e921c93f357bbb.png)

⑯与步骤⑧相同，将本地仓库与远程仓库关联起来：

```bash
git remote add origin 远程仓库链接bash
```

![](https://i-blog.csdnimg.cn/blog_migrate/9ae50dd24ba4d60fb9b4e287547faef4.png) ⑰提交大文件：

```bash
git push -u origin masterbash
```

提交成功，如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/b93c8cb33d40894ec4919e26729d9f48.png)

⑱大文件提高成功之后，继续提交剩余文件：

```bash
git add .

git commit -m "add project EIC" -a

git push -u origin master
bash
```

提交成功，如下图所示：

![](https://i-blog.csdnimg.cn/blog_migrate/a3ee38152c9e9306c2320d87563b9219.png)

![](https://i-blog.csdnimg.cn/blog_migrate/80b04b09c6cbac7a4b1767be96ae5df5.png) 同上，如果只在提交时出错，要么多试几次，要么使用代理（见步骤⑩）。

到此为止，我们就实现了上传，刷新GitHub界面就可以看到自己的仓库了：

![](https://i-blog.csdnimg.cn/blog_migrate/a5fe959e385ea2f4cdd68d62973ab792.png)

另外也可以编写README.md 文件，方便大家交流学习。

哦对了，我上传的是我们组关于组水平脑区功能剖分密度聚类算法的代码，有这方面研究或感兴趣的欢迎交流，原文和GitHub代码在这里：

[Functional Parcellation of Human Brain Precuneus Using Density-Based Clustering | Cerebral Cortex | Oxford Academic (oup.com) https://academic.oup.com/cercor/article/30/1/269/5482328](https://academic.oup.com/cercor/article/30/1/269/5482328 "Functional Parcellation of Human Brain Precuneus Using Density-Based Clustering | Cerebral Cortex | Oxford Academic (oup.com)") [GitHub - JieLi0110/Eigen-clustering-parcellation: Group-level functionally parcellation using density-based clustering, combining density-peaks clustering(DPC) and Laplacian eigenmaps(LE) Group-level functionally parcellation using density-based clustering, combining density-peaks clustering(DPC) and Laplacian eigenmaps(LE) - JieLi0110/Eigen-clustering-parcellation https://github.com/JieLi0110/Eigen-clustering-parcellation.git](https://github.com/JieLi0110/Eigen-clustering-parcellation.git "GitHub - JieLi0110/Eigen-clustering-parcellation: Group-level functionally parcellation using density-based clustering, combining density-peaks clustering(DPC) and Laplacian eigenmaps(LE)")

我的分享就这么多了，欢迎大家一起交流，祝各位早发顶会顶刊，生活开心~~~

实付 元

[使用余额支付](https://blog.csdn.net/weixin_51570804/article/details/)

点击重新获取

扫码支付

钱包余额 0

抵扣说明：

1.余额是钱包充值的虚拟货币，按照1:1的比例进行支付金额的抵扣。  
2.余额无法直接购买下载，可以购买VIP、付费专栏及课程。

[余额充值](https://i.csdn.net/#/wallet/balance/recharge)

举报

[AI 搜索](https://ai.csdn.net/?utm_source=cknow_pc_blog_right_hover) [智能体](https://ai.csdn.net/cmd?utm_source=cknow_pc_blog_right_hover) [AI 编程](https://ai.csdn.net/coding?utm_source=cknow_pc_blog_right_hover) [AI 作业助手](https://ai.csdn.net/homework?utm_source=cknow_pc_blog_right_hover)

隐藏侧栏 ![程序员都在用的中文IT技术交流社区](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_app.png)

程序员都在用的中文IT技术交流社区

![专业的中文 IT 技术社区，与千万技术人共成长](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_wechat.png)

专业的中文 IT 技术社区，与千万技术人共成长

![关注【CSDN】视频号，行业资讯、技术分享精彩不断，直播好礼送不停！](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_video.png)

关注【CSDN】视频号，行业资讯、技术分享精彩不断，直播好礼送不停！

客服 返回顶部

![](https://i-blog.csdnimg.cn/blog_migrate/760d8f5dde90e666f84411b7f81bda08.png) ![](https://i-blog.csdnimg.cn/blog_migrate/fca344b98ec846c8dcf9eb6b9c0f2135.png) ![](https://i-blog.csdnimg.cn/blog_migrate/f3466c644b361830d9de723cee7e5680.png) ![](https://i-blog.csdnimg.cn/blog_migrate/f824578ebf2ca6ecd6fcd9ef35d2f583.png) ![](https://i-blog.csdnimg.cn/blog_migrate/9da8c193c061d289811b759d1357552b.png) ![](https://i-blog.csdnimg.cn/blog_migrate/9900a597c63b2e439117b6ba2326a8f0.png) ![](https://i-blog.csdnimg.cn/blog_migrate/ea193229b856fd23b59580cab6006101.png) ![](https://i-blog.csdnimg.cn/blog_migrate/5c560436199234cd02815c3bddefafdb.png) ![](https://i-blog.csdnimg.cn/blog_migrate/3b53183377574913d798a520bffe692f.png) ![](https://i-blog.csdnimg.cn/blog_migrate/4d58d3494e3052e6cb84520d9b2c5968.png) ![](https://i-blog.csdnimg.cn/blog_migrate/277bf630f7fe38779cdc4bd97a657cca.png) ![](https://i-blog.csdnimg.cn/blog_migrate/8be64a806f61efafc8315358bbaf82cf.png) ![](https://i-blog.csdnimg.cn/blog_migrate/ab5cc4118f08c8294fdfd4424824c58d.png) ![](https://i-blog.csdnimg.cn/blog_migrate/56f432ce6b09423800f9032002c3293a.png) ![](https://i-blog.csdnimg.cn/blog_migrate/84290145d08e246e6f74efbf2496022f.png) ![](https://i-blog.csdnimg.cn/blog_migrate/01591b19c62ef160d970c4181992a828.png) ![](https://i-blog.csdnimg.cn/blog_migrate/4098279e14c1532a918ab3389b683d4a.png) ![](https://i-blog.csdnimg.cn/blog_migrate/b81d07ed2643f01f87a46cc2434cc0e3.png) ![](https://i-blog.csdnimg.cn/blog_migrate/20dda08e12f243005d5322562768d678.png) ![](https://i-blog.csdnimg.cn/blog_migrate/81cdb80fa24b9e36f191f3a501e091c1.png) ![](https://i-blog.csdnimg.cn/blog_migrate/52ed2fc59931e04e75e921c93f357bbb.png) ![](https://i-blog.csdnimg.cn/blog_migrate/9ae50dd24ba4d60fb9b4e287547faef4.png) ![](https://i-blog.csdnimg.cn/blog_migrate/b93c8cb33d40894ec4919e26729d9f48.png) ![](https://i-blog.csdnimg.cn/blog_migrate/a3ee38152c9e9306c2320d87563b9219.png) ![](https://i-blog.csdnimg.cn/blog_migrate/80b04b09c6cbac7a4b1767be96ae5df5.png) ![](https://i-blog.csdnimg.cn/blog_migrate/a5fe959e385ea2f4cdd68d62973ab792.png)