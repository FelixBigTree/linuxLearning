# linux磁盘管理
## 1.1 什么是磁盘
磁盘（disk）是指利用磁记录技术存储数据的存储器。磁盘是计算机主要的存储介质，可以存储大量的二进制数据，并且断电后也能保持数据不丢失。早期计算机使用的磁盘是软磁盘（Floppy Disk，简称软盘），如今常用的磁盘是硬磁盘（Hard disk，简称硬盘）

磁盘运行原理：

简单来说就是多个盘片之间靠主轴连接，电机带动主轴做旋转运动，通过多个磁头臂的摇摆和磁盘的旋转，磁头就可以在磁盘旋转的过程中就读取到磁盘中存储的各种数据
<img width="689" alt="image" src="https://user-images.githubusercontent.com/48283877/123362220-ed71ab80-d5a2-11eb-9f6a-dcf25c4766c5.png">

### 1.1.1 磁盘的扇区、磁道、柱面
- 扇区：硬盘的盘片被磁道划分成多个扇区，硬盘的读写以扇区为基本单位
- 磁道：磁盘的每个盘片被划分为许多同心圆，划分圆的线条叫做磁道

<img width="558" alt="image" src="https://user-images.githubusercontent.com/48283877/123362393-2d389300-d5a3-11eb-865f-6ea46725190f.png">

- 柱面：每一个盘片同一大小的同心圆可以看成连在一起的柱面，磁盘在分区的时候最小单位是柱面，每一个盘片的上下面都可以读取数据，每一个磁头，不可以跨盘面读取数据

<img width="567" alt="image" src="https://user-images.githubusercontent.com/48283877/123362498-6113b880-d5a3-11eb-9a9e-915d3a973942.png">

## 1.2 磁盘管理
Linux磁盘管理通常分成五个步骤：添加硬盘、做RAID或逻辑卷LVM、分区、对分区进行格式化、挂载到文件系统

### 1.2.1 添加硬盘以及做RAID或逻辑卷LVM
- RAID：磁盘阵列（Redundant Arrays of Independent Disks，RAID），磁盘阵列是由很多块独立的磁盘，组合成一个容量巨大的磁盘组，利用个别磁盘提供数据所产生加成效果提升整个磁盘系统效能。利用这项技术，将数据切割成许多区段，分别存放在各个硬盘上

    常见的几种RAID模式
    - RAID0：将数据分散在n个磁盘中，以独立的方式并行读取n个磁盘的数据，理论上，一个由n块磁盘组成的RAID0是单个磁盘性能的n倍
    - RAID1：将数据分别写到两组磁盘中，分别为工作磁盘和镜像磁盘，相当于做了一次冗余，安全性高，但是成本也高
    - RAID10：RAID10兼备了RAID1和RAID0的优点。首先基于RAID1模式将磁盘分为2份，当要写入数据的时候，将所有的数据在两份磁盘上同时写入，相当于写了双份数据，起到了数据保障的作用。且在每一份磁盘上又会基于RAID0技术讲数据分为N份并发的读写，这样也保障了数据的效率

- LVM：Logical Volume Manager（逻辑卷管理）的简写，它是Linux环境下对磁盘分区进行管理的一种机制

Linux的用户经常会遇到一个问题，就是当磁盘分区空间不足了，调整分区大小非常麻烦。而LVM最大的作用就是解决这个问题。LVM将一个或多个硬盘的分区在逻辑上集合，相当于一个大硬盘来使用，当硬盘的空间不够使用的时候，可以继续将其它的硬盘的分区加入其中，这样可以实现磁盘空间的动态管理，相对于普通的磁盘分区有很大的灵活性

### 1.2.2 分区
当硬盘添加成功后，便可以对硬盘进行分区了
#### 1.2.2.1 为什么要分区
- 方便管理：文件种类繁多的时候不容易混乱
- 安全：硬盘出现问题的时候，减少数据损失

#### 1.2.2.2 分区常用命令
fdisk是创建和维护分区表的程序，兼容DOS类型的分区表、BSO或者SUN类型的磁盘列表

  - 更改分区表
  
  `fdisk [选项] <磁盘>
  
  - 列出分区表

  `fdisk [选项] -l [<磁盘>]`
 

<img width="435" alt="image" src="https://user-images.githubusercontent.com/48283877/123366961-bbb11280-d5ab-11eb-8398-0e0013c74989.png">

常用选项如下

<img width="445" alt="image" src="https://user-images.githubusercontent.com/48283877/123367061-e56a3980-d5ab-11eb-999f-349e9474eb58.png">


对某个磁盘分区，如 fdisk /dev/sda，则会出现以下菜单进行选择

<img width="438" alt="image" src="https://user-images.githubusercontent.com/48283877/123367140-0763bc00-d5ac-11eb-85b4-107e2d4ddd48.png">

其中，常用操作如下

<img width="236" alt="image" src="https://user-images.githubusercontent.com/48283877/123367171-15b1d800-d5ac-11eb-91bc-c25c46e89d5b.png">


### 1.2.3 格式化
#### 1.2.3.1 什么是格式化

格式化一般是指逻辑格式化，它是指根据用户选定的文件系统，在磁盘的特定区域写入特定数据，以达到初始化磁盘或磁盘分区、清除原磁盘或磁盘分区中所有文件的一个操作。

文件系统指操作系统用于明确存储设备或分区上的文件的方法和数据结构：即在存储设备上组织文件的方法

#### 1.2.3.2 格式化常用命令

`mkfs [选项] [-t <类型>] [文件系统选项] <设备> [<大小>]`

创建一个Linux 文件系统

<img width="381" alt="image" src="https://user-images.githubusercontent.com/48283877/123367442-83f69a80-d5ac-11eb-92e0-f76fe794f885.png">

### 1.2.4 挂载
#### 1.2.4.1 什么是挂载
Linux 系统中一切皆文件，所有文件都放置在以根目录为树根的树形目录结构中。在 Linux 看来，任何硬件设备也都是文件，它们各有自己的一套文件系统（文件目录结构）。挂载，指的就是将设备文件中的顶级目录连接到 Linux 根目录下的某一目录，访问此目录就等同于访问设备文件

#### 1.2.4.2 mount命令

```
 mount [-lhV]
 mount -a [选项]
 mount [选项] [--source] <源> | [--target] <目录>
 mount [选项] <源> <目录>
 mount <操作> <挂载点> [<目标>]
```

用默认方法将/dev/usb 挂载到 /mnt/usb

`mount /dev/usb /mnt/usb`

<img width="436" alt="image" src="https://user-images.githubusercontent.com/48283877/123367985-84436580-d5ad-11eb-8e6a-6df42e9abf61.png">

提示挂载点不存在，先创建一个再重新挂载

`mkdir -p /mnt/usb`

<img width="460" alt="image" src="https://user-images.githubusercontent.com/48283877/123368117-c5d41080-d5ad-11eb-942a-f9674f28e41a.png">

提示特殊设备不存在
