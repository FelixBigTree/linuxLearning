# 1 task1
主要讲述了linux的发展历程和优势
- 网址导航：https://github.com/datawhalechina/team-learning-program/blob/master/Linux/1.什么是Linux.md


# 2 task2
虚拟机的安装以及linux环境的配置

## 2.1 安装虚拟机以及linux系统
1.使用Oracle VM VirtualBox，由于我用的是mac，所以选择OS X hosts 安装，网址导航：https://www.virtualbox.org/wiki/Downloads
<img width="1189" alt="image" src="https://user-images.githubusercontent.com/48283877/121765145-750af380-cb7b-11eb-8849-b01d9aa1fbf5.png">
2.准备Ubuntu ISO镜像文件，网址导航：https://ubuntu.com/download/desktop#download
<img width="1221" alt="image" src="https://user-images.githubusercontent.com/48283877/121765206-cf0bb900-cb7b-11eb-8f4b-2b579cef7d58.png">
3.按照教程安装即可，教程导航：https://github.com/datawhalechina/team-learning-program/blob/master/Linux/2.Linux安装.md

如果是在mac上下载安装了virtualbox，然后正常设置了iso镜像，启动时报错Kernel driver not installed (rc=-1908)，解决方法如下
- 1、重启mac
- 2、打开系统偏好设置>>安全性与隐私
- 3、会有一行Oracle的权限授权，点击允许
<img width="860" alt="image" src="https://user-images.githubusercontent.com/48283877/121765676-37a86500-cb7f-11eb-9ebe-e85d119ee61e.png">

## 2.2 全屏设置
- 安装完成后，发现virtual box 窗口最大化了，可是里面的窗口并没有最大化，看着很累
我的做法是设置scale to 150%，然后把窗口分辨率调整到1600 x 1200 （4:3），看着舒服多了
设置完了以后是这样的
<img width="1200" alt="image" src="https://user-images.githubusercontent.com/48283877/121766225-295c4800-cb83-11eb-8bc4-25d86b846a1b.png">

## 2.3 软件安装
- Linux下常见的两种软件安装方式，分别是软件包安装和源码编译安装

### 2.3.1 软件包安装
- Linux下配置开发环境较便利，其中一个原因是Linux有很好的包管理工具。包管理工具可以在操作系统中提供安装、升级，卸载软件的方法
- 在Linux下，DPT和RPM是最为常见的两种包管理工具，分别应用于基于deb软件包的Linux发行版和基于rpm软件包的Linux发行版
- 另外还有arch linux系列的Pacman包管理工具

#### 2.3.1.1 deb
- 基于 Debian 操作系统 (UBUNTU) 的 DEB 软件包管理工具－ Dpkg，全称为 Debian Package
- 是一个可以安装、构建、删除及管理 Debian 软件包的命令行工具，用来制作 Debian 包的工具，同时也可以查看、解压 Debian 包
下面是一些dpkg的普通用法
- 安装一个Debian安装包（其中-i等价于--install）

  `dpkg -i <package.deb>`

- 列出<package.deb>的内容中包含的文件结果（其中-c等价于--contents）

  `dpkg -c <package.deb>`
  
- 从<package.deb>中提取包裹信息的详细信息，包括软件名称、版本以及大小等（其中-l等价于--info）

  `dpkg -l <package.deb>`
  
- 移除一个已安装的包裹（软件名称可通过dpkg -I命令查看，其中-r等价于--remove）

  `dpkg -r <package.deb>`
  
- 完全清除一个已安装的包裹。和 remove 不同的是，remove 只是删掉数据和可执行文件，purge 另外还删除所有的配制文件

  `dpkg -P <package.deb>`

- 列出<package>安装的软件包安装的所有文件（软件名称可通过dpkg -I命令查看，其中-L等价于--listfiles）
  
  `dpkg -L <package.deb>`
  
- 查看<package>软件包的信息（软件名称可通过dpkg -I命令查看，其中-l等价于--list）
  
  `dpkg -l <package.deb>`
  
- 显示已安装包裹的详细信息。同时请看 apt-cache 显示 Debian 存档中的包裹信息，以及 dpkg -I 来显示从一个 .deb 文件中提取的包裹信息。（软件名称可通过dpkg -I命令查看，其中-s等价于--status）
  
  `dpkg -s <package.deb>`
  
- 重新配制一个已经安装的包裹，如果它使用的是 debconf (debconf 为包裹安装提供了一个统一的配制界面)
  
  `dpkg -reconfigure <package.deb>`
