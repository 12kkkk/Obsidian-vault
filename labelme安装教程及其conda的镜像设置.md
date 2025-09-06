## 安装labelme
在windows下用Anaconda安装labelme
1、在windows下打开anaconda prompt，找不到可以在搜索中进行搜索
![[attachment file（image、pdf)/IMG-labelme安装教程及其conda的镜像设置-2025.09.06.png]]
2、在命令行中查看conda版本
conda -V
3、创建labelme虚拟环境
conda create -n labelme python=3.9.18
指定python版本为3.9.18
查看已经创建的虚拟环境
conda list env 
![[attachment file（image、pdf)/IMG-labelme安装教程及其conda的镜像设置-2025.09.06-1.png]]
4、查看python版本
python -V
![[attachment file（image、pdf)/IMG-labelme安装教程及其conda的镜像设置-2025.09.06-2.png]]
5、激活创建的labelme虚拟环境
conda activate labelme
6、安装labelme需要的附属包,-i后指定镜像，加快下载速度
conda install pyqt5 pillow -i https://pypi.tuna.tsinghua.edu.cn/simple
7、安装labelme
pip install labelme -i https://pypi.tuna.tsinghua.edu.cn/simple
8、指定版本安装
pip install labelme==3.16.7
## conda镜像设置
配置anaconda prompt、linux中的conda下载镜像
查看当前镜像
 conda config --show channels
 ![[attachment file（image、pdf)/IMG-labelme安装教程及其conda的镜像设置-2025.09.06-3.png]]
若返回的鹅结果只有defaults，说明用的国外源。

添加镜像源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/