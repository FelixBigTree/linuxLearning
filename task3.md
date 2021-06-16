# linux 用户及组管理
## 1. 用户与用户组
### 1.1 什么是用户
- Linux是多用户多任务的操作系统，多个用户可以同时登陆执行不同任务
- 用户需要使用系统资源则需向系统管理员申请账户进入系统
- 不同的用户则拥有不同的权限
- 用户又分超级用户和普通用户，超级用户即系统管理员root

### 1.2 什么是用户组
当我们需要让多个用户都拥有某一个权限，就可以把他们放进同一个用户组里，方便集中管理
其中用户组分两种：
- 一种是主用户组（primary group），主用户组的信息保存在/etc/passwd 文件中
- 一种是次用户组（secondary group），次用户组的信息保存在/etc/group 中。

当用户被创建之后默认属于同名用户组，即主用户组，后来再将该用户加入其他用户组的话，加入的用户组为该用户的次用户组。

- 为了后续演示，将'datawhale'创建为次用户组，并且创建用户datawhale1，加入组datawhale

    `sudo groupadd -g 888 datawhale`
    
    `sudo useradd datawhale`
    
    `sudo gpasswd -a datawhale1 datawhale`

    `grep datawhale /etc/group`
  
<img width="464" alt="image" src="https://user-images.githubusercontent.com/48283877/122245403-46cd4100-cef8-11eb-8505-a8e61e9bd859.png">

### 1.3 用户与用户组的关系
每个用户在创建时都会自动属于一个用户组，此外用户与用户组之间的关系又可以分为以下四种:
- 一对一：一个用户可以存在一个组中，是组中的唯一成员
- 一对多：一个用户可以存在多个用户组中，此用户具有这多个组的共同权限
- 多对一：多个用户可以存在一个组中，这些用户具有和组相同的权限
- 多对多：多个用户可以存在多个组中，也就是以上 3 种关系的扩展


## 2. 用户ID与组ID
在Linux系统中，并不是通过用户名来识别用户的，而是通过用户ID来判断是哪个用户的，用户 datawhale 会被赋予一个名为Datawhale 的用户组，且成为该新建用户组的唯一成员，同时UID和GID会被分别写入/etc/passwd和/etc/group中

### 2.1 用户的增删修改

  - 为了演示，删除datawhale组

    `sudo groupdel datawhale`
    
    `sudo useradd datawhale`
    
    `grep datawhale /etc/group`
    
<img width="399" alt="image" src="https://user-images.githubusercontent.com/48283877/122246817-76307d80-cef9-11eb-9c8d-bcf379506935.png">


- 主目录：用户的起始工作目录，用户登录后有操作权限的访问目录

- 注释性描述：这个字段并没有什么实际的用途。在不同的Linux 系统中，这个字段的格式并没有统一。在许多Linux系统中，这个字段存放的是一段任意的注释性描述文字，用做finger命令的输出

- 登陆shell：用户登录后，要启动一个进程，负责将用户的操作传给内核，这个进程是用户登录到系统后运行的命令解释器或某个特定的程序，即Shell

- 通常情况下，UID是递增的，上一个是1000，下一个则是1001   

  比如新增一个用户
    
    `sudo useradd datawhale1`
    
<img width="416" alt="image" src="https://user-images.githubusercontent.com/48283877/122247441-eb03b780-cef9-11eb-8a83-4e47864ab6cc.png">


可以发现，uid递增了1


另外，系统管理员的UID为0

    `grep root /etc/passwd`
    
<img width="544" alt="image" src="https://user-images.githubusercontent.com/48283877/122247805-361dca80-cefa-11eb-9fb0-8bc925293c7e.png">


- 删除用户

    `userdel 选项 用户名`
    
例如，删除用户datawhale1

    `sudo userdel datawhale1`
    
<img width="410" alt="image" src="https://user-images.githubusercontent.com/48283877/122248523-b3493f80-cefa-11eb-951e-8901ffe49d9f.png">


- 修改用户

    `usermod 选项 用户名`
    
<img width="989" alt="image" src="https://user-images.githubusercontent.com/48283877/122248711-d83db280-cefa-11eb-9070-f45cd9212749.png">


- 修改用户密码

    `passwd 选项 用户名`
    
<img width="941" alt="image" src="https://user-images.githubusercontent.com/48283877/122248875-f99e9e80-cefa-11eb-9ca0-808b83f66e20.png">


### 2.2 用户组管理
- 添加用户组

    `groupadd 选项 用户组`

    例如，新增一个data用户组
        `sudo groupadd data`

<img width="379" alt="image" src="https://user-images.githubusercontent.com/48283877/122249549-89dce380-cefb-11eb-86a2-1ede7ad18f29.png">

- 删除用户组

    `groupdel 组名`
    
不能使用 groupdel 命令随意删除群组。此命令仅适用于删除那些 "不是任何用户初始组" 的群组，换句话说，如果有群组还是某用户的初始群组，则无法使用 groupdel 命令成功删除。倘若该群组中仍包括某些用户，则必须先删除这些用户后，方能删除群组

打个比方，往组data添加两个用户

    ```
    sudo useradd data1
    sudo useradd data2
    sudo gpasswd -a data1 data
    sudo gpasswd -a data2 data
    ```
    
<img width="505" alt="image" src="https://user-images.githubusercontent.com/48283877/122250335-2901db00-cefc-11eb-9e87-a35c92d93133.png">


此时，如果删除data组
    
    `sudo groupdel data`

<img width="520" alt="image" src="https://user-images.githubusercontent.com/48283877/122250611-61a1b480-cefc-11eb-808e-e4ee19371e3c.png">

尴尬，好吧，组是可以删除的，只是在使用删除组的时候要养成好的习惯。先删除用户后再删除组！！！


- 修改用户组属性

    `groupmod 选项 用户组`
    
<img width="276" alt="image" src="https://user-images.githubusercontent.com/48283877/122250877-a0376f00-cefc-11eb-8d24-c4444b02156c.png">

- 切换用户组

    `newgrp 目标用户组`
    
newgrp 指令类似 login 指令:**newgrp 命令可以从用户的附加组中选择一个群组，作为用户新的初始组。
**欲使用 newgrp 指令切换群组，用户必须是该群组的用户，否则将无法登入指定的群组。
单一用户要同时隶属多个群组，需利用交替用户的设置。
若不指定群组名称，则 newgrp 指令会登入该用户名称的预设群组
    
