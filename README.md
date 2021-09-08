# HYFU-GPU-Server

介绍
====
HYFU-GPU-Server采用依瞳AI平台（介绍见pdf文件）进行计算资源调配和用户文件管理，可以直接通过网页访问服务器，主要使用其中的代码开发功能访问服务器，用户建立自己的独立容器，并在其中进行文件管理、搭配环境和跑代码。


新用户使用指南
==============

### 1. 代码开发 --> 创建开发环境 --> SSH/Jupyter --> 进入服务器
  a) 引擎类型推荐选择horovod, 多GPU分布式运行程序参考 https://horovod.ai/getting-started/
  
  b) 创建的开发环境最好一直运行中，否则再次创建还需要重新配置网络
  
     /home/username/    %为用户自己的默认文件夹，装软件、配环境、存文件都应在这个文件夹里操作，与其他用户隔离，其他用户访问不到
     /data/dataset/     %大型的公开数据集下载放在这里，方便大家一起调用
   
### 2. 使用root权限
    sudo + ...
   
### 3. 配置网络并安装ping工具，测试网络
    sudo vim /etc/resolv.conf
    %% 把 nameserver 114.114.114.114 插入到第一行，才能联网     (这里的命令建议手打，直接复制会出错)
    %% vim文本编辑器命令： i是切换到插入模式，Esc退出插入模式，:wq 保存并退出vim， :q!强制退出并忽略所有更改， :e!放弃所有修改并打开原来文件
    sudo apt update
    sudo apt-get install iputils-ping
    
### 4. 下载和安装Anaconda（配置环境工具）
    a) 确认下载目录home/user/
    b) 下载Anaconda
	    wget -P /tmp https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh  
    c）安装Anaconda
  	  bash Anaconda3-2021.05-Linux-x86_64.sh
    d) 安装完成后输入yes，初始化conda（新手建议yes）
    e) source ~/.bashrc   %使环境变量生效的命令

### 5. 卸载Anaconda
    rm -rf ~/anaconda3 ~/.condarc ~/.conda ~/.continuum
    
### 6. 修改ssh密码
    sudo passwd username
