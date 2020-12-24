# Aria2+天翼网盘——使用Aria2下载再自动上传到天翼网盘实现离线下载的功能

## 使用方法


### 安装Aria2需要的软件
```
yum install -y wget curl ca-certificates
```

### 安装Aria2
```wget -N git.io/aria2.sh && chmod +x aria2.sh
./aria2.sh
```

### 安装Python3.8
```
yum -y groupinstall "Development Tools"
yum -y install zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel readline-devel tk-devel gdbm-devel db4-devel libpcap-devel xz-devel libffi-devel
cd /tmp
wget https://www.python.org/ftp/python/3.8.7/Python-3.8.7.tgz
tar -zxf Python-3.8.7.tgz
cd Python-3.8.7
./configure --prefix=/usr/local/python3
make && make install
ln -s /usr/local/python3/bin/python3.8 /usr/bin/python3
ln -s /usr/local/python3/bin/pip3.8 /usr/bin/pip3
```

### 安装天翼网盘CLI工具
```
yum -y install git
cd ~
git clone https://github.com/Aruelius/cloud189.git
cd cloud189
pip3 install -r requirements.txt
```

### 天翼网盘CLI配置账号、文件夹
```
python3 main.py
mkdir aria2
cd aria2
```

### 配置Aria2的下载完成事件脚本
改/root/.aria2c/aria2.conf，找到“下载完成后执行的命令”，把clean.sh替换为upload-189.sh。
如果你不是用这个脚本安装的，没有这一行，就新增一行，写下面的内容
```
# 下载完成后执行的命令
on-download-complete=/root/.aria2c/upload-189.sh
```

把本仓库upload-189.sh的内容写到/root/.aria2c/upload-189.sh，保存完记得授予执行权限  
```chmod +x /root/.aria2c/upload-189.sh```

改完配置必须重启aria2   
使用命令```bash ~/aria2.sh```执行脚本，然后按照提示重启。

感谢：
[https://github.com/P3TERX/aria2.sh](https://github.com/P3TERX/aria2.sh)
[https://github.com/Aruelius/cloud189](https://github.com/Aruelius/cloud189)
[https://www.moerats.com/archives/482/](https://www.moerats.com/archives/482/)

也可以到我博客看看  
[https://haoduck.com/698.html](https://haoduck.com/698.html)