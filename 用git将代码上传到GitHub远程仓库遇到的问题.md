
  114  git init -b main    # 初始化本地文件夹，使得git能够管理文件夹，并重命名本地分支为main，与github分支一致
  115  git add .    # 将本地文件夹下的全部文件上传到git暂存区
  116  git commit -m "Python"   #
  119  git commit -m "Python"
  120  git remote add origin https://github.com/12kkkk/zero-learning-note-repository.git
  121  git push -u origin main

上诉命令报错为
fatal: unable to access 'https://github.com/12kkkk/zero-learning-note-repository
.git/': SSL certificate problem: unable to get local issuer certificate

即通常是由于 Git 无法验证 GitHub 的 SSL 证书，可能是因为你的系统缺少根证书（CA certificates），或者网络环境（如公司代理）干扰了 SSL 验证。

我们采用改用SSH连接github远程仓库：HTTPS 可能会受证书问题影响，而 SSH 更稳定：

生成 SSH 密钥​​
在git命令行中输入
![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06.png]]
回车完成配置
![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-9.png]]
生成密钥文件，文件在
![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-10.png]]

cat 密钥文件地址，查看密钥内容

Github添加密钥
在 GitHub → ​**​Settings​**​ → ​**​SSH and GPG keys​**​ → ​**​New SSH key​**​，粘贴并保存。
github登录，来到home页面
![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-11.png]]

![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-12.png]]
提示成功添加密钥
![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-13.png]]
连接远程仓库

![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-14.png]]

![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-15.png]]
测试SSH是否连接

![[attachment file（image、pdf)/IMG-用git将代码上传到GitHub远程仓库遇到的问题-2025.09.06-16.png]]

结果为链接成功

此外我们也可以暂时禁用ssl
此命令会全局禁用 SSL 验证。如果只想针对某个仓库禁用，可以在克隆时使用以下命令：

GIT_SSL_NO_VERIFY=true git clone https://github.com/username/repo.git