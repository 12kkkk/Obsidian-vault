---
title: "Linux 系统下 Git 的详细安装步骤和基础设置指南"
source: "https://blog.csdn.net/qq_45657541/article/details/147254349"
author:
  - "[[qq_45657541]]"
published: 2025-04-20
created: 2025-09-08
description: "文章浏览阅读2.9k次，点赞14次，收藏19次。Linux 系统下 Git 的详细安装步骤和基础设置指南_linux安装git"
tags:
  - "clippings"
---
---

![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/1e771fae9ba046a081c33dc72a9f3e98.png#pic_center)

---

---

## 一、安装 Git

### 1\. Debian/Ubuntu 系统

```bash
# 更新软件包列表
sudo apt update

# 安装 Git
sudo apt install git -y

# 验证安装
git --version
bash12345678
```

• 输出示例： `git version 2.39.0`

---

### 2\. CentOS/RHEL 系统

```bash
# 启用 EPEL 仓库（若未启用）
sudo yum install epel-release -y

# 安装 Git
sudo yum install git -y

# 或使用 dnf（CentOS 8+）
sudo dnf install git -y

# 验证安装
git --version
bash1234567891011
```

---

### 3\. Fedora 系统

```bash
# 使用 dnf 安装
sudo dnf install git -y

# 验证安装
git --version
bash12345
```

---

### 4\. Arch/Manjaro 系统

```bash
# 使用 pacman 安装
sudo pacman -Syu git -S

# 验证安装
git --version
bash12345
```

---

### 5\. 其他方式：源码编译安装（适用于所有发行版）

1. 安装依赖：
	```bash
	# Debian/Ubuntu
	sudo apt install curl-devel expat-devel gettext-devel openssl-devel zlib-devel -y
	# CentOS/RHEL
	sudo yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel -y
	bash12345
	```
2. 下载并解压 Git 源码：
	```bash
	wget https://mirrors.edge.kernel.org/pub/software/scm/git/git-2.39.0.tar.gz
	tar -zxvf git-2.39.0.tar.gz
	cd git-2.39.0
	bash123
	```
3. 编译并安装：
	```bash
	make prefix=/usr/local all
	sudo make prefix=/usr/local install
	# 验证安装
	git --version
	bash12345
	```

---

## 二、基础配置

### 1\. 设置全局用户名和邮箱

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 验证配置
git config --global --list
bash12345
```

---

### 2\. 配置 SSH 密钥（用于 GitHub/GitLab 等）

1. 生成 SSH 密钥：
	```bash
	ssh-keygen -t ed25519 -C "your.email@example.com"
	bash1
	```
	• 按提示保存密钥到默认路径（ `~/.ssh/id_ed25519` ）。  
	• 设置密钥密码（可选）。
2. 将公钥添加到 [GitHub](https://so.csdn.net/so/search?q=GitHub&spm=1001.2101.3001.7020) /GitLab：  
	• 复制公钥内容：
	```bash
	cat ~/.ssh/id_ed25519.pub
	bash1
	```
	• 登录 GitHub → Settings → SSH and GPG Keys → 添加新 SSH Key。
3. 测试 SSH 连接：
	```bash
	ssh -T git@github.com
	bash1
	```
	• 成功提示： `Hi username! You've successfully authenticated.`

---

### 3\. 配置 Git 别名（简化命令）

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.st status
git config --global alias.lg "log --oneline --graph --all"
bash1234
```

• 示例： `git st` 等同于 `git status` 。

---

### 4\. 启用自动换行符转换（解决跨平台换行符问题）

```bash
git config --global core.autocrlf input    # Linux/macOS
git config --global core.safecrlf warn     # 检测混合换行符
bash12
```

---

## 三、高级设置

### 1\. 配置差异工具（如 Meld）

1. 安装 Meld：
	```bash
	# Debian/Ubuntu
	sudo apt install meld -y
	# CentOS/RHEL
	sudo yum install meld -y
	bash12345
	```
2. 配置 Git 调用 Meld：
	```bash
	git config --global merge.tool meld
	git config --global mergetool.meld.path "/usr/bin/meld"
	bash12
	```

---

### 2\. 配置 Git 代理（解决网络问题）

```bash
# HTTP/HTTPS 代理
git config --global http.proxy http://127.0.0.1:7890
git config --global https.proxy https://127.0.0.1:7890

# SOCKS5 代理（如 Clash）
git config --global http.proxy socks5://127.0.0.1:7890
git config --global https.proxy socks5://127.0.0.1:7890

# 取消代理
git config --global --unset http.proxy
git config --global --unset https.proxy
bash1234567891011
```

---

### 3\. 配置钩子（Hooks）自动化操作

1. 示例：在提交前运行代码检查  
	• 进入仓库的 `.git/hooks` 目录：
	```bash
	cd /path/to/repo/.git/hooks
	bash1
	```
	• 创建 `pre-commit` 文件：
	```bash
	#!/bin/sh
	echo "Running code checks..."
	npm test  # 示例：运行测试
	bash123
	```
	• 赋予执行权限：
	```bash
	chmod +x pre-commit
	bash1
	```

---

## 四、常见问题与解决方法

### 1\. 安装失败：E: Unable to locate package git

• 解决：更新软件源并重试：

```bash
sudo apt update && sudo apt install git -y
bash1
```

---

### 2\. 权限错误：Permission denied (publickey)

• 解决：

1. 确认 SSH 密钥已添加到 `ssh-agent` ：
	```bash
	eval "$(ssh-agent -s)"
	ssh-add ~/.ssh/id_ed25519
	bash12
	```
2. 检查公钥是否正确添加到 GitHub/GitLab。

---

### 3\. Git 版本过旧

• 升级 Git：

```bash
# Debian/Ubuntu
sudo add-apt-repository ppa:git-core/ppa -y
sudo apt update && sudo apt upgrade git -y

# Fedora
sudo dnf upgrade git -y
bash123456
```

---

### 4\. 终端提示 git: command not found

• 解决：  
• 检查是否已安装： `which git` 。  
• 若未安装，通过上述方法重新安装。  
• 确保 Git 路径在环境变量中（ `echo $PATH` ）。

---

## 五、卸载 Git

### 1\. 通过包管理器卸载

• Debian/Ubuntu：

```bash
sudo apt remove git -y
bash1
```

• CentOS/RHEL：

```bash
sudo yum remove git -y
bash1
```

### 2\. 手动卸载（源码安装）

```bash
sudo rm -rf /usr/local/bin/git
sudo rm -rf /usr/local/share/doc/git
bash12
```

---

## 六、学习资源推荐

1. Pro Git 电子书（免费）：  
	[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)
2. GitHub 官方教程：  
	[https://guides.github.com/](https://guides.github.com/)
3. Git 命令速查表：  
	[https://education.github.com/git-cheat-sheet-education.pdf](https://education.github.com/git-cheat-sheet-education.pdf)

---

通过以上步骤，您可以在 Linux 系统上快速安装并配置 Git，满足日常开发需求！

---

打赏作者

¥1 ¥2 ¥4 ¥6 ¥10 ¥20

扫码支付： ¥1

获取中

扫码支付

您的余额不足，请更换扫码支付或 [充值](https://i.csdn.net/#/wallet/balance/recharge?utm_source=RewardVip)

打赏作者

实付 元

[使用余额支付](https://blog.csdn.net/qq_45657541/article/details/)

点击重新获取

扫码支付

钱包余额 0

抵扣说明：

1.余额是钱包充值的虚拟货币，按照1:1的比例进行支付金额的抵扣。  
2.余额无法直接购买下载，可以购买VIP、付费专栏及课程。

[余额充值](https://i.csdn.net/#/wallet/balance/recharge)

举报

 [![](https://csdnimg.cn/release/blogv2/dist/pc/img/toolbar/Group-dark.png) 点击体验  
DeepSeekR1满血版](https://ai.csdn.net/?utm_source=cknow_pc_blogdetail&spm=1001.2101.3001.10583) 隐藏侧栏 ![程序员都在用的中文IT技术交流社区](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_app.png)

程序员都在用的中文IT技术交流社区

![专业的中文 IT 技术社区，与千万技术人共成长](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_wechat.png)

专业的中文 IT 技术社区，与千万技术人共成长

![关注【CSDN】视频号，行业资讯、技术分享精彩不断，直播好礼送不停！](https://g.csdnimg.cn/side-toolbar/3.6/images/qr_video.png)

关注【CSDN】视频号，行业资讯、技术分享精彩不断，直播好礼送不停！

客服 返回顶部

![](https://i-blog.csdnimg.cn/direct/1e771fae9ba046a081c33dc72a9f3e98.png#pic_center)