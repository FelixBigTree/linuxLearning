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
