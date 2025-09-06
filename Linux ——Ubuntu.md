1、初步了解Linux
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06.png]]
Linux发行版
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-1.png]]远程登录linux系统
FinalShell
https://www.hostbuf.com/t/988.html
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-2.png]]

WSL （windows for Linux）----Ubuntu
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-3.png]]

直接利用计算机的硬件，不需要像虚拟机用虚拟化技术来构建虚拟化环境

linux的目录结构
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-4.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-5.png]]
对于centos7，place - computer就是根目录/
命令、命令行
命令的通用格式: command [-option]  [parameter]  命令-选项-参数


su username 切换用户
sudo useradd username 创建用户
sudo passwd username 修改用户密码
基础命令
ls    选项l、h、a，参数：指定目录   展开目录下的内容
1、ls -l /home      list表示
2、ls -h                  表明大小 
3、ls -a：带.的文件为隐藏文件       all全部

ls -la      ls -lh    ls -ah    ls -lah   组合使用 
* ls命令后面添加参数目录磕查看指定目录的内容


cd：切换目录
pwd：查看当下工作目录

相对路径、绝对路径
绝对路径：从根目录开始写，到目标目录结束，如：cd /home/bio-zero
相对目录：从当前目录开始写，到目标目录，如我当前工作目录为home目录，需要切换到bio-zero目录，可以cd  bio-zero

特殊路径符
假设当前我在home目录下，home目录下有bio-zero目录
cd ./bio-zero
cd ..  ：切换到上一级目录
cd ../.. :切换到上二级目录
cd ~ :切换到（用户的）home目录
cd ~/bo-zero ：切换到（用户的）home目录下的bio-zero目录下

mkdir命令
mkdir [-p] 路径
mkdir dir1 在当前工作目录下创建dir1目录
mkdir ./dir1/dir2 在当前工作目录下的dir1目录下创建dir2目录
mkdir ~/dir3  在用户的home目录下创建dir3
mkdir ../dir4 在当前工作目录上一级目录创建dir4

* ctrl+l   /  clear ： 清屏

创建多级目录 添加 -p选项
mkdir -p /dir5/dir6/dir7 在当前工作目录下创建dir5，在dir5下创建dir6，在dir6下创建dir7目录

touch命令
touch ./test.txt  在当前目录下创建test.txt文件
touch ~/dir5/test1.txt   在用户的home目录下的dir5目录内创建test1.txt文件

cat命令：查看文件内容     cat 路径     查看全部内容
cat ./test.txt

more命令
more翻页查看内容
more /etc/services

cp命令：复制文件、文件夹，cp -r 目录1 目录2
-r：复制的为文件夹时加入
目录1为需要复制的文件、文件夹
目录2为需要粘贴的文件、文件夹
cp ./test.txt ./dir1/test_cp_1.txt
cp -r ./dir5 ./dir3

move命令：移动文件、文件夹
move 目录1 目录2
目录1为需要移动的文件文件夹
目录2为目标文件、文件夹
move ./dir4 ./dir3

rm命令：删除文件、文件夹
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-6.png]]

rm -r  ./dir1 ./dir3

通识符  *
通识符用于做模糊匹配
test*：匹配任意以test开头的内容
****test：匹配任意以test结尾的内容
*test *：匹配任意包含test的内容

rm -r dd* :移除全部以dd开头的文件夹

rm ./****txt ：表示删除以txt后缀的文件



rm -rf 慎用

查找命令

which命令： 查看命令的程序文件存放目录（命令的本质就是可执行文件）
which cd
which pwd

文件查找命令：find
find 开始路径 -name "filename"：表示从某一级目录开始查找，-name表示以文件名查找，"filename"表示要查找的文件名
find / -name "test"

find和通配符的混合使用查找文件
find / -name "****test     "   表示查找以test结尾的文件全部文件

find命令按文件大小查找
find / -size +10k：查找大于10KB的文件  （小写k）
find / -size +100M：查找大于100MB的文件
find / -size -1G：查找小于1GB的文件

grep命令：从文件中通过关键字过滤文件的行，返回含有关键字的行
grep -n "keyword" pathway
-n参数可选，有则返回符合条件的行
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-7.png]]

wc命令：统计文件行数、单词数量、字符数、bytes数、
wc -c/-m/-w/-l pathway
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-8.png]]

管道符 " | ":将管道符左边的命令的输出结果，作为右边命令的输入

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-9.png]]
红框内的文件路径通过管道符的输出结果给出
管道符左边命令：只要命令有输出结果就行
管道符右边命令：只要命令需要输入就行
如： ls | grep -n test :可用于查找符合要求文件
ls -l | wc -l :可以用于查看文件数量
ls -l /usr | wc -l ：可以查看/usr目录下文件数

管道符可以嵌套使用
cat test.txt | grep -n "zero" | grep -n 'ab'
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-10.png]]

echo命令：输出指定内容，同print
echo “hello linux”

反引号 : echo后的命令也会当字符输出，加入反引号，以命令输出
echo ` pwd`
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-11.png]]

重定向符
1、> :将左侧命令的结果，覆盖写到右侧文件中，echo " hello linux" > test.txt
test.txt的内容清除后在写入hello Linux
2、>>:将左侧命令的结果，追加写到右侧文件中，添加写入
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-12.png]]
tai命令：查看文件的尾部内容，即查看文件的更新内容

tai -f /-num 路径
-f 表示持续跟踪
-num表示查看尾部多少行，默认10行
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-13.png]]


vim/vi 编辑器
vim pathway 打开需要编辑的文件
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-14.png]]


![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-15.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-16.png]]

vim命令模式
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-17.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-18.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-19.png]]


Linux用户和权限

root用户：超级管理员
拥有最大的系统操作权限
普通用户只在其home目录下权限相对较自由，出了home 目录很难直线权限

su - username 切换用户
-表示加载环境变量
切换用户后需要回到原用户用exit命令
exit

sudo命令：获得root用户的权限
sudo 命令

需要为普通用户配置sudo认证
sudo认证
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-20.png]]

用户和用户组
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-21.png]]
用户组的创建的删除
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-22.png]]

用户管理
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-23.png]]useradd username 创建用户
userdel username 删除用户
id username命令：查看用户的组
usermod -aG user group username ：修改用户组，usermod -aG group1 zero 将zero用户添加到用户组group1中
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-24.png]]

查看系统现有用户
getent passwd  最下面的一般为我们自己创建的用户
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-25.png]]

查看系统中有哪些用户组
getent group
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-26.png]]

查看文件的权限控制
认识权限信息
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-27.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-28.png]]

序号1：开头为-表示是一个文件，d表示为文件夹，l为软连接
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-29.png]]
序号一10个位置，第一个表示文件夹（d）、文件（-）、软连接（l）

其余9个三个三个为一组权限，分别表示用户权限、用户组权限、其他权限

前3个中表示为用户权限，若有权限标出字母，无权限用-表示，如rxw表示该用户有rxw权限，若为r-w为有r、w权限，无x权限

其中r：read：读权限，w：write 写权限，x：execute 志向权限

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-30.png|552]]

修改权限信息
chmod命令
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-31.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-32.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-33.png]]

chmod 751、chmod 777、chmod 111修改权限的含义
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-34.png]]

修改文件、文件夹的用户、用户组
chown命令
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-35.png]]


Linux快捷键
1、ctrl+c强制停止、取消命令、重新编写命令
2、ctrl+d退出账户登录、退出某些特定的程序专属页面
3、history：查看历史命令
4、！+ 历史命令中含有的字母（开头），从历史命令中匹配最近使用的命令执行，！t
5、ctrl+r检索历史命令中最符合输入的命令
6、光标移动
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-36.png]]
7、清屏（不清除历史）ctrl+l / clear


Linux安装软件
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-37.png]]

centos
yum命令
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-38.png]]

如：sudo yum -y install wget
sudo yum remove wget
sudo yum search  wget

ubuntu安装软件,同样需要root权限
apt install/remove/search wget  

systemctl命令：控制软件的启动、停止、开机自启
语法：systemctl start / stop /status/enable/disable 服务名
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-39.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-40.png]]
如systemctl start ssh 启动ssh服务

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-41.png]]



软连接（类似于windows的快捷方式）
ln -s 目录1（被链接文件、文件夹） 目录2（ 要连接去的目的地）
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-42.png]]


日期和时间
date命令

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-43.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-44.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-45.png]]


切换时区：root权限
修改时区需要切换到root用户
1、rm -f /etc/localtime
2、ln -s /usr/share/zoneinfo/Aisa/Shanghai  /etc/localtime

IP地址
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-46.png]]
特殊的IP地址
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-47.png]]

主机名，查看主机名：命令hostname
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-48.png]]
Linux修改主机名
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-49.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-50.png]]

域名解析
如百度的网址为baidu.com，输入www.baidu.com可以访问百度的地址
域名解析的机制
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-51.png]]

配置主机名和IP地址的映射，从而实现通过主机名对IP地址的访问
管理员运行记事本——打开C\Windows\System32\drivers\etc\hosts文件——在最后一行加入服务器IP地址（空格）服务器主机名——保存即可
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-52.png]]
用finalshell 连接服务器
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-53.png]]


虚拟机固定IP地址
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-54.png]]ping命令
ping命令检查指定服务器是否可以联通
ping -c ip/hostname
-c：表示检查次数，默认无数次（不添加）
如检擦百度网站baidu.com
ping -c 3 baidu.com
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-55.png]]

一般用于测试、检查某个服务器是否是联通的

wget命令
wget -b url
-b：后台下载
url下载连接
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-56.png]]

curl -O url
下载文件时：curl -O url
发送请求时：curl url
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-57.png]]
发送请求等同于打开网站，只是不能形成网页。


端口
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-58.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-59.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-60.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-61.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-62.png]]

查看端口占用
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-63.png]]

用nmap查看端口
nmap + IP地址
namp 127.0.0.1 查看本机的端口占用情况
netstat -anp
netstat -anp | grep 22

进程管理
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-64.png]]
Linux中查看进程
命令：ps -e/-f
-e：显示全部进程
-f：以完全格式化的形式展示信息
ps -ef 列出全部进程的全部信息
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-65.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-66.png]]

利用管道符查看指定的进程，任意字符都可以
ps -ef | grep tail :查找tail命令进程
ps -ef | grep 9877:查找9877进程号的进程

关闭进程
kill -9 进程id
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-67.png]]

查看主机状态

查看主机系统资源占用
top命令
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-68.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-69.png]]![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-70.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-71.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-72.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-73.png]]查看磁盘的信息监控
df -h
-h：加入人性化的单位显示
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-74.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-75.png]]

CPU、磁盘的信息
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-76.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-77.png]]网络状态监控
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-78.png]]
sar -n DEV 
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-79.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-80.png]]

环境变量
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-81.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-82.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-83.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-84.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-85.png]]
PATH包含一系列路径，就是执行程序的搜索路径
比如当前环境中运行cd命令，就会在PATH中的一系列路径中搜索cd执行文件进行执行


$ 符号

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-86.png]]
$ 符取到对应的环境变量
如echo $ PATH   \     echo $ PWD

echo $ {PATH}ABC
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-87.png]]


自行配置变量
如PATH中的路径中添加特定地方的程序，即可在你的环境中运行相关程序

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-88.png]]
临时配置：export MYNAME=zero
永久配置
1、当前用户生效，配置在当前用户：~/bashrc文件中
2、所有用户生效，配置在系统：/etc/profile文件中
并通过语法source配置文件进行立刻生效，或重新登录

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-89.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-90.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-91.png]]


自定义PATH环境变量
1、创建一个文件夹，mkdir myevn
2、创建一个文件mkhaha
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-92.png]]
3、编辑文件内容echo “哈哈哈”
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-93.png]]
3、查看文件（及其权限）
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-94.png]]
可以知道当前用户不可执行，即无x
4、设置权限
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-95.png]]
5、执行文件
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-96.png]]
6、将这个脚本文件添加到PATH中，允许在其他地方执行
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-97.png]]
7、在任何目录都可以执行
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-98.png]]
利用finalshell在linux中进行上传和下载

finalshell中从服务器中下载文件到windows中
1、finalshell中的文件找到需要下载的文件
2、右键下载
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-99.png]]
3、根据下载目录找到下载的文件
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-100.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-101.png]]

finalshell中从windows长传到服务器（linux）上传文件
直接将要长传的文件拖到对应文件夹内
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-102.png]]![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-103.png]]

用rz、sz命令上传、下载
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-104.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-105.png]]
rz根据弹框上传





解压和压缩文件
1、用tar命令压缩、解压tar、gzip文件
2、用zip、unzip命令压缩、解压zip文件

压缩格式
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-106.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-107.png]]![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-108.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-109.png]]

zip压缩包的压缩、解压
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-110.png]]
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-111.png]]

scp命令
通过ssh协议进行多台服务器之间进行cp命令的文件复制，功能就是在不同的Linux服务器之间传输文件
![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-112.png]]

![[attachment file（image、pdf)/IMG-Linux ——Ubuntu-2025.09.06-113.png]]