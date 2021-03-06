# linux文件和目录管理
## 1.1 linux 目录
Linux中，目录为树状结构。树状目录以 / 为起始，也称为根目录，是Linux文件系统的入口，每一个文件和目录都从这里开始

因为目录繁多，各类软件安装，配置都可能存在混乱的情况，所以产生了FHS（Filesystem Hierarchy Standard）组织

FHS制定了目录规范，什么文件应该放在什么目录，根据FHS标准，Linux目录一般可分为以下四种交互状态：

<img width="581" alt="image" src="https://user-images.githubusercontent.com/48283877/122492023-9f473000-d017-11eb-8e9d-f5eee8dd40a6.png">

- static:不可变的

- variable:可变的

- shareable:可分享的，“可共享”文件是指可以存储在一台主机上并在其他主机上使用的文件，例如，用户主目录中的文件是可共享的

- unshareable:不可分享的“，不可共享”文件是指那些不可共享的文件，例如设备锁文件。

## 1.2 目录详解
在Linux中，常使用 ls 命令来查看目录结构，例如查看根目录下的目录0结构
  
  ` ls / `
  
<img width="495" alt="image" src="https://user-images.githubusercontent.com/48283877/122641249-a6b12b00-d136-11eb-95a3-7dd3897482ce.png">

这些目录中：
- / - 根目录，是linux文件系统的入口，每个文件和目录都从这里开始
- /bin - 基本用户命令二进制文件目录，包含系统管理员和用户都可以使用的命令
- /etc - 配置文件目录，包含所有程序所需的配置文件，配置文件用于控制程序操作的本地文件，它必须是静态的，不能是可执行的二进制文件
- /boot - 引导文件，目录包含系统启动过程中所需的所有内容，但不包括启动时不需要的配置文件和映射安装程序
- /dev - 设备文件，（device的缩写），该目录下存放的是linux的外部设备，包括终端设备、usb、连接到系统的任何设备。linux中访问设备的方式和访问文件的方式是相同的
- /lib - 库文件，包含引导系统的运行根文件系统中命令所需的共享库映像，即位于/bin和/sbin中的二进制文件，这些文件可以被很多程序共享
- /sbin - 系统二进制文件，包含由系统管理员使用的二进制可执行文件
- /proc - 进程信息文件，包含系统进程的相关信息，是系统内存的映射
- /opt - 可选择文件，用于安装附加应用程序软件包
- /lost+found - 次目录通常为空，当系统非法关机后，才会存放一些文件
- /srv - 服务器数据文件，包含服务器特定服务相关的数据
- /var - 变量文件，这个目录下可以找到内容可能增长的文件，包括
    - /var/log - 系统日志文件
    - /var/lib - 数据库文件
    - /var/mail - 电子邮件
    - /var/spool - 打印队列
    - /var/lock - 锁文件
    - /var/tmp - 多次重新启动需要的临时文件
- /tmp - 包含系统和用户创建的临时文件，当系统重新启动时，这个目录下的文件都将被删除
- /home - 用户目录，所有用户都用home来存储个人文件
- /usr - 用户程序目录，包含二进制文件、库文件、文档、二级程序的源代码
- /mnt - 挂载目录，此目录主要作为挂载点使用，通常包括系统引导后被挂载的文件系统的挂载点
- /media - 可移动媒体设备，用于挂载可移动设备的临时目录


## 1.3 linux文件
### 1.3.1 linux文件类型
linux中一共有六种文件类型，分别是普通文件、目录文件、链接文件、设备文件、套接字文件、管道文件；
- 1.普通文件：包括纯文本文件（ASCII）、二进制文件（binary）、数据格式的文件(data)；
- 2.目录文件：其实就是linux中的目录，目录也是文件；
- 3.链接文件：符号链接是指向系统上其它文件的引用，类似windows下的快捷方式；
- 4.设备文件：linux中的硬件设备（硬盘、鼠标等）也都被表示为文件（设备文件），一般存放在/dev目录下；
- 5.管道文件：管道是一种最基本的IPC机制，作用于有血缘关系的进程之间；一般的管道都是单向通信的，无法实现双向通信的功能；
- 6.套接字文件：提供进程间通信方法的文件，套接字可以实现两端通信

六种文件中，普通文件、目录文件、链接文件占用存储空间；而设备文件、管道文件、套接字文件是伪文件，不占用磁盘空间

### 1.3.2 文件权限
以普通文件为例，我进的是/usr/bin目录，，使用 ls -l 命令：

  ` ls -l`
  
可以看到文件信息的第一列是 -rwx 形式，其中第一个字符'-'表示这个文件为普通文件，后面的字符表示文件权限。第一个字符也可以是其他格式，不同字符代表不同的文件类型
<img width="1023" alt="image" src="https://user-images.githubusercontent.com/48283877/122642959-9b163200-d13f-11eb-95aa-38a9a6b7e351.png">

## 1.4 命令
- ls

  `ls 选项 地址`
  
  其中，选项参数如下
  - -a： 全部文件，连同隐藏文件（开头为.的文件）一起列出
<img width="512" alt="image" src="https://user-images.githubusercontent.com/48283877/122643265-7458fb00-d141-11eb-93d6-d8b5fe8b952d.png">

  - -d： 仅仅列出目录本身，而不是列出目录内的文件数据
<img width="293" alt="image" src="https://user-images.githubusercontent.com/48283877/122643275-85097100-d141-11eb-8ac8-c1ee80eee550.png">

  - -l： 长数据串列出，包含文件的属性与权限等等
<img width="462" alt="image" src="https://user-images.githubusercontent.com/48283877/122643284-8fc40600-d141-11eb-8e3e-6b387cecbbdd.png">

- cd

  `cd 地址`
  
  切换路径
  
- pwd

  查看当前路径
  
  其中，选项参数如下
  - -P ：显示出确实的路径，而非使用连结 (link) 路径

    `pwd -P`
    
- mkdir

  创建一个新目录
  
  `mkdir 选项 目录名称`
  
  其中，选项参数如下
  - -m：配置文件权限
  - -p：直接将所需要的目录（包含上一级目录递归创建）
  
  例如，在桌面创建一个新目录bag
  
  `cd /home/felix/桌面`
  `mkdir -p bag`
  
<img width="358" alt="image" src="https://user-images.githubusercontent.com/48283877/122643508-bafb2500-d142-11eb-8f6e-31316ec9ba3f.png">

- rmdir

  删除目录
  
  `rmdir 选项 目录名称`
  
  其中，选项参数如下
  - **-p ：**连同上一级『空的』目录也一起删除

  例如，删除在桌面的bag目录
  
  `rmdir bag`
  
- cp

  复制文件
  
  `cp 选项  源文件 目标地址/文件`
  
  其中，选项参数如下
  
  <img width="666" alt="image" src="https://user-images.githubusercontent.com/48283877/122643724-05c96c80-d144-11eb-9b9d-b15f41881385.png">


- rm

  删除文件
  
  `rm 选项 文件或目录`
  
  其中，选项参数如下
  
  <img width="504" alt="image" src="https://user-images.githubusercontent.com/48283877/123051416-5b4b9500-d434-11eb-82f1-bf38fd9893f1.png">

- mv

  移动文件
  
  `mv 源地址/文件 目标地址/文件`
  
  其中，选项参数如下
  
  <img width="553" alt="image" src="https://user-images.githubusercontent.com/48283877/123051519-761e0980-d434-11eb-88c2-cd31875c13ad.png">

- cat

  阅览文件
  
  `cat 选项 目标文件地址`
  
  其中，选项参数如下
  
  <img width="559" alt="image" src="https://user-images.githubusercontent.com/48283877/123051610-8f26ba80-d434-11eb-9915-e2816247f19f.png">

- ln

  1.软链接(windows下的快捷方式创建)，如果删除原文件，则对应的软链接文件也会消失
  
  `ln -s test.txt test_softlink`

  2.硬链接，相当于给原文件取了个别名，其实两者是同一个文件，删除二者中任何一个，另一个不会消失；对其中任何一个进行更改，另一个的内容也会随之改变，因为这两个本质上是同一个文件，只是名字不同
  
  `ln test.txt test_hardlink`
  









