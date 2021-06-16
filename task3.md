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



