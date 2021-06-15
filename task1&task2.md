# 1 task1（基本为摘录）
主要讲述了linux的发展历程和优势
- 网址导航：https://github.com/datawhalechina/team-learning-program/blob/master/Linux/1.什么是Linux.md

## 1.1 什么是linux
Linux，全称为GNU/Linux，是一种免费使用和自由传播的类UNIX操作系统
我们常说的Linux，指的是Linux内核，一个基于POSIX的多用户、多任务、支持多线程和多CPU的操作系统

## 1.2 linux的优点
- 开源免费：完全免费的操作系统，且源代码开放，任何人都可以随意修改
- 多任务：可以使多个程序同时独立运行
- 多用户：每个用户对于自己的文件设备有特殊的权利，用户之间使用互不影响
- 安全可靠：代码开源，所有用户都可以参与漏洞修复，同时用户管理权限使得安全风险降低
- 稳定：可以持续运行很久而不易崩溃
- 多平台：可以运行在多种硬件平台上
- 方便：在线安装软件包十分方便，一行命令即可，同时配置环境也很快捷
- 开源软件多：大多数开源软件的首要适配平台都是linux

## 1.3 发展历程
20世纪80年代，计算机硬件的性能不断提高，PC的市场不断扩大，当时可供计算机选用的操作系统主要有Unix、DOS和macOC这几种。

Unix价格昂贵，不能运行于PC；DOS显得简陋，且源代码被软件厂商严格保密；MacOS是一种专门用于苹果计算机的操作系统。此时，计算机科学领域迫切需要一个更加完善、强大、廉价和完全开放的操作系统。由于供教学使用的典型操作系统很少，因此当时在荷兰当教授的美国人AndrewS.Tanenbaum编写了一个操作系统，名为MINIX，为了向学生讲述操作系统内部工作原理。

MINIX虽然很好，但只是一个用于教学目的的简单操作系统，而不是一个强有力的实用操作系统，然而最大的好处就是公开源代码。全世界学计算机的学生都通过钻研MINIX源代码来了解电脑里运行的MINIX操作系统，芬兰赫尔辛基大学大学二年级的学生Linus Torvalds就是其中一个。

在吸收了MINIX精华的基础上，Linus于1991年写出了属于自己的Linux操作系统，版本为Linux0.01，是Linux时代开始的标志。他利用Unix的核心，去除繁杂的核心程序，改写成适用于一般计算机的x86系统，并放在网络上供大家下载，1994年推出完整的核心Version1.0，至此，Linux逐渐成为功能完善、稳定的操作系统，并被广泛用

## 1.4 常用发行版
- Debian：老牌发行版，非常稳定，适合用于服务器。

- Ubuntu：是Debian的一款衍生版，侧重于它在这个市场的应用，在服务器、云计算、甚至一些运行Ubuntu Linux的移动设备上很常见。于2004年9月首次公布的。属于热门发行版之一，因其图形界面开发较完善以及良好的社区支持，很受初接触Linux的人群青睐。

- CentOS：一种对 RHEL（Red Hat Enterprise Linux）源代码再编译的产物，由于 Linux 是开发源代码的操作系统，并不排斥样基于源代码的再分发，CentOS 就是将商业的 Linux 操作系统 RHEL 进行源代码再编译后分发，并在 RHEL 的基础上修正了不少已知的漏洞。

- Fedora：Linux（第七版以前为Fedora Core）是由Fedora项目社区开发、红帽公司赞助，目标是创建一套新颖、多功能并且自由（开放源代码）的操作系统。Fedora是商业化的Red Hat Enterprise Linux发行版的上游源码。

- Kali：Linux是Debian的一款衍生版。旨在渗透测试和数字取证。它预先构建了用于渗透测试的多种工具。

- Arch：一款采用滚动发行方式的操作系统，只要安装一次就够了，每当发行了某个新版本，就可以升级发行版，无需重新安装。Pacman是Arch Linux的软件包管理器。Arch Linux既支持X86处理器架构，又支持X86_64架构，安装程序可以从光盘或U盘来运行。


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

 #### rpm
 - rpm是 redhat 、fedora、suse 的格式，全称为Redhat PackageManager ，是由Redhat公司提出的用于管理Linux下软件包的软件
 - Linux安装时，除了几个核心模块以外，其余几乎所有的模块均通过RPM完成安装
 下面是一些rmp的使用指令
 - 安装需要的包文件，-iv 在安装过程中显示正在安装的文件信息，-ivh 在安装过程中显示正在安装的文件信息及安装进度
 
  `rpm -i <package.rpm>`
 
 查询指令：

- a 查询所有已经安装的包以下两个附加命令用于查询安装包的信息
- i 显示安装包的信息
- l 显示安装包中的所有文件被安装到哪些目录下
- s 显示安装包中的所有文件状态及被安装到哪些目录下
- p 查询的是安装包的信息
- f 查询的是已安装的某文件信息

列出需要升级的包

  `rpm -U`
  
升级 example.rpm 软件包
  
  `rpm -Uvh example.rpm`
  
列出需要验证的包
  
  `rpm -V`
  
## 2.4 编译源码安装
源代码安装软件的优点如下
- 可以获得最新的软件，及时修复bug
- 根据用户的需求，灵活定制软件功能
1. tar -xzvf soft.tar.gz #解压一般会生成一个soft目录
2. ./configure #检查环境变量及配置编译选项
3. make #源代码编译成二进制文件
4. make install #将make编译出来的文件安装到指定位置(或默认位置) 卸载：make uninstall 或 手动删除，由于软件可能将文件分散地安装在系统的多个目录中，往往很难把它删除干净， 最好在编译前进行配置，指定软件将要安装到目标路径：./configure --prefix=目录名，这样可以使用“rm -rf 软件目录名”命令来进行干净彻底的卸载

## 2.5 在线安装
## 2.5.1 apt包管理
由于操作系统中软件包存在复杂的依赖关系，为了解决软件包的依赖性问题和获取问题，APT顺势出现了。 APT 是 Ubuntu Linux 中的命令行软件包管理工具，用于获取、安装、编译、卸载和查询 Deb 软件包，以及检查软件包的依赖关系
apt常用命令如下：
- 更新本地索引，即更新/var/lib/apt/lists 里边的内容
  
  `sudo apt-get update`
  
- 更新所有软件包
  
  `sudo apt-get upgrade `
  
- 安装软件
  
  `sudo apt-get install xx`
  
- 卸载包
  
  `sudo apt-get remove xx`
  
- 卸载并彻底清除
  
  `sudo apt-get remove --purge name`
  
- 清理下载文件的存档
  
  `sudo apt-get clean`
  
## 2.5.2 换源
- 在线安装，如apt包管理的软件仓库地址可能在国外，国内连接速度较慢。所以可以将软件仓库地址改为国内源码库
- Ubuntu 的软件源配置文件是 /etc/apt/sources.list。将系统自带的该文件做个备份，将该文件替换为下面内容，即可使用 TUNA 的软件源镜像。

用gedit命令打开sources.list文件
  `sudo gedit /etc/apt/sources.list`

将内容改为下面：
  
  ```
  # 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-updates main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-backports main restricted universe multiverse
  deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-security main restricted universe multiverse

  # 预发布软件源，不建议启用
  # deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
  # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ focal-proposed main restricted universe multiverse
  ```
  
## 2.6 开源软件
### 2.6.1 效率工具
#### 2.6.1.1 搜狗输入法
- 安装fcitx
  
  `sudo apt-get install fcitx`
  
- 进入搜狗输入法官网，选择linux版下载deb文件(ubuntu系统)，网址导航：https://pinyin.sogou.com/linux/?r=pinyin
按照教程来即可，注意在安装搜狗的时候，终端要先切换到安装包所在路径，输入命令：
  
  `sudo dpkg -i sogoupinyin_版本号_amd64.deb`
  
- 如果提醒缺少依赖，输入如下命令：
  
  `sudo apt -f install`
  
#### 2.6.1.1 Terminator
- terminator可以在同一个窗口分割出多个终端，每个终端都是独立的，适合大屏使用
  
  `sudo apt-get install terminator`
  
- 设置默认Terminal为Terminator
  
  ```
  gsettings set org.gnome.desktop.default-applications.terminal exec   /usr/bin/terminator
  gsettings set org.gnome.desktop.default-applications.terminal exec-arg "-x"
  ```

常用快捷键如下
- Ctrl+Alt+T 打开终端
- Ctrl+l 相当于clear，即清屏
- Shift+Ctrl+T 打开新的标签页
- Shift+Ctrl+W 关闭标签页
- Shift+Ctrl+C 复制
- Shift+Ctrl+V 粘贴
- Shift+Ctrl+N 打开新的终端窗口
- Shift+Ctrl+o 上下拆分屏幕
- Shift+Ctrl+e 左右拆分屏幕
- Shift+Ctrl+w 关闭当前窗口
- Shift+Ctrl+q 关闭整个终端
- F11 全屏切换
- Ctrl + Page Down/ Page Up 切换标签页

  
### 2.6.2 开发工具
#### 2.6.2.1 git
Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目
- 命令行安装
  
  `sudo apt-get install git`
  
#### 2.6.2.2 vim
Vim是从 vi 发展出来的一个文本编辑器。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。和Emacs并列成为类Unix系统用户最喜欢的编辑器
- 首先将vim的源码克隆下来，这里因为github可能很慢，使用码云的镜像
  
  `git clone https://gitee.com/mirrors/vim.git`
  
- 安装gcc和各依赖库
  
  `sudo apt-get install gcc`
  
  `sudo apt-get install libncurses5-dev python-dev python3-dev libatk1.0-dev libbonoboui2-dev libcairo2-dev libx11-dev libxpm-dev libxt-dev`
  
其中libbonoboui2-dev提示无法找到位置，考虑增加镜像源，文件路径为/etc/apt/sources.list，一般情况下，该文件是只读的，直接使用vi或getit打开，无法修改，所以需要先获得root权限
  
  `sudo getit /etc/apt/sources.list`
  
添加镜像源并保存
  
  `deb http://archive.ubuntu.com/ubuntu/trusty main universe restricted multiverse
  
更新镜像源头

  `sudo apt-get update`
  
然后重新安装libbonoboui2-dev，成功

- 配置与安装

注意，这个命令要进入vim路径下执行
  
  ```
  sudo ./configure --with-features=huge --enable-multibyte --enable-rubyinterp --enable-pythoninterp --enable-python3interp --enable-luainterp --enable-    cscope --enable-gui=gtk3 --enable-perlinterp --with-python-config-dir=/usr/lib/python2.7/config-x86_64-linux-gnu/ --with-python3-config-dir=/usr/lib/python3.6/config-3.6m-x86_64-linux-gnu/ --prefix=/usr/local/vim8
  ```
  
- --with-features=huge：支持最大特性
- --enable-rubyinterp：打开对 ruby 编写的插件的支持 
- --enable-pythoninterp：打开对 python 编写的插件的支持 
- --enable-python3interp：打开对 python3 编写的插件的支持 
- --enable-luainterp：打开对 lua 编写的插件的支持 
- --enable-perlinterp：打开对 perl 编写的插件的支持 
- --enable-multibyte：打开多字节支持，可以在 Vim 中输入中文 
- --enable-cscope：打开对cscope的支持 
- --enable-gui=gtk3 表示生成采用 GNOME3 风格的 gvim 
- --with-python-config-dir=/usr/lib/python2.7/config-x86_64-linux-gnu/ 指定 python 路径 
- --with-python3-config-dir=/usr/lib/python3.6/config-3.6m-x86_64-linux-gnu/ 指定 python3路径(这里可以根据自己的版本做更改) 
- --prefix=/usr/local/vim8：指定将要安装到的路径
  
## 2.7 常用终端快捷键
<img width="508" alt="image" src="https://user-images.githubusercontent.com/48283877/122026604-f45b2a00-cdfc-11eb-953c-02a36ec06b63.png">
