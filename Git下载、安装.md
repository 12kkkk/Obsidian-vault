## git下载
当需要下载安装git时，在浏览器搜索git下载，找到git官网
找到git下载界面[Git - Downloading Package](https://git-scm.com/downloads/win)
![[IMG-Git下载、安装and20250830165443460.png]]
找到电脑对应的版本，选择下载
![[IMG-Git下载、安装and20250830165520294.png]]

## git安装
右键git安装包，选择以管理员身份运行
![[IMG-Git下载、安装and20250830165716336.png]]
弹出安装页面，点击next

![[IMG-Git下载、安装and20250830165810627.png]]
选择安装盘符、位置
![[IMG-Git下载、安装and20250830165836733.png]]
勾选需要的选项
![[IMG-Git下载、安装and20250830165959518.png]]
选择初始文件夹，或者选择"`Don't create a Start Menu folder`" 打勾不要文件夹
![[IMG-Git下载、安装and20250830170254661.png]]
选择文本编辑器，默认为vim编辑器
![[IMG-Git下载、安装and20250830170358302.png]]##### 决定初始化新项目(仓库)的主干名字，第一种是让 Git 自己选择，名字是 `master` ，但是未来也有可能会改为其他名字；第二种是我们自行决定，默认是 `main`，当然，你也可以改为其他的名字。一般默认第一种，点击 [next] 到第七步。
![[IMG-Git下载、安装and20250830170514463.png]]
设置path环境变量
![[IMG-Git下载、安装and20250830170647005.png]]
翻译：Use Git from Git Bash only 
This is the most cautious choice as your PATH will not be modified at all. You w only be able to use the Git command line tools from Git Bash.
仅从 Git Bash 使用 Git
这是最谨慎的选择，因为您的 PATH 根本不会被修改。您将只能使用 Git Bash 中的 Git 命令行工具。

Git from the command line and also from 3rd-party software
(Recommended) This option adds only some minimal Git wrappers to your PATH to avoid cluttering your environment with optional Unix tools.
You will be able to use Git from Git Bash, the Command Prompt and the Windov PowerShell as well as any third-party software looking for Git in PATH.
从命令行以及第三方软件进行 Git
（推荐）此选项仅将一些最小的 Git 包装器添加到PATH中，以避免使用可选的 Unix 工具使环境混乱。
您将能够使用 Git Bash 中的 Git，命令提示符和 Windov PowerShell 以及在 PATH 中寻找 Git 的任何第三方软件。

Use Git and optional Unix tools from the Command Prompt 
Both Git and the optional Unix tools will be added to your PATH.
Warning: This will override Windows tools like "find"and "sort". Only use this option if you understand the implications.
使用命令提示符中的 Git 和可选的 Unix 工具
Git 和可选的 Unix 工具都将添加到您的 PATH 中。
警告：这将覆盖 Windows 工具，例如 "find" and "sort". 仅在了解其含义后使用此选项。

第一种是仅从 Git Bash 使用 Git。这个的意思就是你只能通过 Git 安装后的 Git Bash 来使用 Git ，其他的什么命令提示符啊等第三方软件都不行。

第二种是从命令行以及第三方软件进行 Git。这个就是在第一种基础上进行第三方支持，你将能够从 Git Bash，命令提示符(cmd) 和 Windows PowerShell 以及可以从 Windows 系统环境变量中寻找 Git 的任何第三方软件中使用 Git。推荐使用这个。

第三种是从命令提示符使用 Git 和可选的 Unix 工具。选择这种将覆盖 Windows 工具，如 “ find 和 sort ”。只有在了解其含义后才使用此选项。一句话，适合比较懂的人折腾。
————————————————

                            版权声明：本文为博主原创文章，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
                        
原文链接：https://blog.csdn.net/mukes/article/details/115693833



[Git 详细安装教程（详解 Git 安装过程的每一个步骤）_git安装-CSDN博客](https://blog.csdn.net/mukes/article/details/115693833)