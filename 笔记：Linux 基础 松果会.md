# 笔记：Linux 基础 | 松果会
[](#视频地址 "视频地址")视频地址
--------------------

B站黑马：[缘起](https://b23.tv/av213091208/p118) —— [缘灭](https://b23.tv/av213091208/p141)

[](#一、Linux-简介 "一、Linux 简介")一、Linux 简介
--------------------------------------

Linux 是一套免费使用和自由传播的类 Unix 操作系统，是一个基于 POSIX 和 UNIX 的多用户、多任务、支持多线程和多 CPU 的操作系统

Linux 不仅系统性能稳定，还开放了源码

**桌面操作系统**

*   Windows（用户数量最多）
*   Mac OS
*   Linux

**服务器操作系统**

*   UNIX
*   Linux
*   Windows Server

**移动设备操作系统**

*   Android（基于Linux、开源）
*   IOS（苹果公司开发、不开源）

**嵌入式操作系统**

*   Linux（机顶盒、路由器、交换机）

【图解】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721112920496.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721112920496.png)

### [](#Linux-系统版本 "Linux 系统版本")Linux 系统版本

**内核版**

*   由Linus Torvalds及其团队开发、维护
*   开源免费
*   负责控制硬件

**发行版**

*   基于Linux内核版进行扩展
*   由各个Linux厂商开发和维护的
*   有收费版本和免费版本

市面上较为知名的Linux发行版如下：

*   Ubuntu：以桌面应用为主
*   RedHat：应用最广泛、收费
*   CentOS：RedHat的社区版、免费
*   openSUSE：对个人完全免费、图形界面华丽
*   Fedora：功能完备、快速更新、免费
*   红旗Linux：北京中科红旗软件技术有限公司开发（中科红旗承诺，红旗Linux桌面操作系统 v11及后续迭代版本永久向个人及家庭用户免费提供）

【图解】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721151343628.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721151343628.png)

[](#二、Linux-安装 "二、Linux 安装")二、Linux 安装
--------------------------------------

Linux系统安装方式

*   物理机安装：直接将操作系统安装到服务器硬件上
*   虚拟机安装：通过虚拟机软件安装

**虚拟机**是指通过软件模拟的具有完整硬件系统功能的、运行在一个完全隔离环境中的完整计算机系统。虚拟机技术的核心思想是将物理计算机的资源（如处理器、内存、存储等）进行虚拟化，使多个虚拟机可以共享这些资源，并在其上运行不同的操作系统和应用程序

可以通过虚拟机软件来模拟计算机硬件

常用的虚拟机软件：VMWare、VirtualBox…

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721182825817.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721182825817.png)

[](#三、安装SSH连接工具 "三、安装SSH连接工具")三、安装SSH连接工具
-----------------------------------------

SSH（Secure Shell）是一种网络协议，用于在不安全的网络中安全地进行远程登录和数据传输。它通过加密和身份验证机制，确保数据在传输过程中的安全性

常用的SSH连接工具：putty、filezilla、xshell、finalshell

通过SSH连接工具就可以实现从本地连接到远程的Linux服务器

这里选择使用finalshell作为SSH连接工具

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721184522862.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721184522862.png)

然后使用FinalShell连接Linux

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721184801284.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721184801284.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185020990.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185020990.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185105224.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185105224.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185159433.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185159433.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185246363.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721185246363.png)

[](#四、Linux目录结构 "四、Linux目录结构")四、Linux目录结构
-----------------------------------------

在Linux系统中，/是所有目录的顶点

> *   bin 存放二进制可执行文件
> *   boot 存放系统引导时使用的各种文件
> *   dev 存放设备文件
> *   etc 存放系统配置文件
> *   home 存放系统用户的文件
> *   lib 存放程序运行所需的共享库和内核模块
> *   opt 额外安装的可选应用程序包所放置的位置
> *   root 超级用户目录
> *   sbin 存放二进制可执行文件，只有root用户才能访问
> *   tmp 存放临时文件
> *   usr 存放系统应用程序
> *   var 存放运行时需要改变数据的文件，例如日志文件

【图解】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721193044740.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721193044740.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721194624566.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721194624566.png)

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721195140040.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230721195140040.png)

[](#五、Linux-常用命令 "五、Linux 常用命令")五、Linux 常用命令
--------------------------------------------

*   文件目录操作命令
*   拷贝移动命令
*   打包压缩命令
*   文本编辑命令
*   查找命令

常用命令列表

| 类别 | 命令 | 英文全称 | 含义 | 语法 | 示例 |
| --- | --- | --- | --- | --- | --- |
| 文件目录操作 | cd | change directory | 切换用户当前工作目录 | `cd \[-L | \[-P \[-e\]\]\] \[dir\]` | `cd /` |
| 文件目录操作 | cp | copy | 将源文件或目录复制到目标文件或目录中 | `cp(选项)(参数)` | `cp file /usr/men/tmp/file1` |
| 文件目录操作 | rm | remove | 用于删除给定的文件和目录 | `rm(选项)(参数)` | `rm -rf testdir` |
| 文件目录操作 | mv | move | 对文件或目录移动或重命名 | `mv(选项)(参数)` | `mv file_1.txt /home/office/` |
| 文件目录操作 | rmdir | remove directory | 用来删除空目录 | `rmdir(选项)(参数)` | `rmdir -p www/Test` |
| 文件目录操作 | touch | touch | 更新文件的时间标签和创建新的空文件 | `touch(选项)(参数)` | `touch ex2` |
| 文件目录操作 | mkdir | make directory | 用来创建目录 | `mkdir(选项)(参数)` | `mkdir -m 700 /usr/meng/test` |
| 文件目录操作 | clear | clear | 清除当前屏幕终端上的任何信息 | `clear` | 输入clear后当前终端上的任何信息就会被清除 |
| 文件目录操作 | li | list | 显示目录内容列表 | `ls [选项] [文件名...]` | `ls -l` |
| 文件目录操作 | tree | tree | 树状图列出目录的内容 | `tree(选项)(参数)` | `tree /private/ -L 1` |
| 文件目录操作 | cat | cat | 显示文件内容和连接多个文件并打印到标准输出 | `cat [OPTION]... [FILE]...` | `cat -s test.log` |
| 文件目录操作 | pwd | print work directory | 显示当前工作目录的绝对路径 | `pwd [-LP]` | `pwd` |
| 文件目录操作 | man | man | 查看Linux中的指令帮助 | `man(选项)(参数)` | `man 3 sleep` |

🔥Linux命令有很多，如何快速了解相关命令，可通过查询[命令列表](https://wangchujiang.com/linux-command/hot.html)详细快速了解

🔥Linux命令有很多，如何快速找到具有某项功能的命令，可通过查询[Linux命令大全](https://www.linuxcool.com/)详细快速了解

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722151611969.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722151611969.png)

### [](#Linux-使用技巧 "Linux 使用技巧")Linux 使用技巧

*   按下Tab键可自动补全
    
*   连按两次Tab键可给出操作提示
    
*   使用上下箭头快速调出曾经使用过的命令
*   使用clear命令或者`ctrl+l`快捷键实现清屏
*   使用`ctrl+a`实现定位到命令行行首，使用`ctrl+e`实现定位到命令行行尾

### [](#Linux-命令格式 "Linux 命令格式")Linux 命令格式

`command [-options][parameter]`

_说明：_

*   command：命令名
*   \[-options\]：选项，可用来对命令进行控制，可省略
*   \[parameter\]：参数，可以是零个或多个

**注意：**  命令名、选项和参数用空格分隔，`[]`代表可选

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722153728560.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722153728560.png)

### [](#文件目录操作 "文件目录操作")文件目录操作

`ls`显示指定目录下的内容，语法：`ls [-al][dir]`

**说明：**  -a 显示所有文件及目录（.开头的隐藏文件也会列出），-l 除文件名称外，同时将文件型态（d开头表示目录、-开头表示文件）、权限、拥有者、文件大小等信息详细列出

**注意：**  由于使用ls命令时经常需要加入`-l`选项，所以Linux为`ls -l`命令提供了一种简写方式，即`ll`

`cd`用于切换当前工作目录，即进入指定目录，语法：`cd [dirName]`

**说明：**  `~`表示用户的home目录，`.`表示当前所在目录，`..`表示当前目录的上一级目录

`cat`用于显示文件内容，语法：`cat [-n] fileName`

**说明：**  -n：由1开始对所有输出的行数编号

`more`以分页的形式显示文件内容，语法：`more fileName`

**操作说明：**  回车键即向下滚动一行，空格键即向下滚动一屏，b即返回上一屏，q或者ctrl+c即退出more

`tail`查看文件末尾的内容，语法：`tail [-f] fileName`

**说明：**  -f动态读取文件末尾内容并显示，通常用于日志文件的内容输出

`mkdir`用于创建目录，语法：`mkdir [-p] fileName`

**说明：**  -p是确保目录名称存在，不存在就创建一个。通过此选项，可以实现多层目录同时创建

`rmdir`删除空目录，语法：`rmdir [-p] dirName`

**说明：**  -p是确保当子目录被删除后使父目录为空目录的话则一并删除

`rm`删除文件或目录，语法：`rm [-rf] name`

**说明：**  -r：将目录及目录中所有文件（目录）逐一删除，即递归删除，-f：无需确认，直接删除

### [](#拷贝移动命令 "拷贝移动命令")拷贝移动命令

`cp`用于复制文件或目录，语法：`cp [-r] source dest`

**说明：**  -r：如果复制的是目录需要使用此选项，此时将复制该目录下所有的子目录和文件

**案例：**  `cp -r itcast/ itheima/`是将itcast目录和目录下所有目录及文件复制到itheima目录下，`cp -r itcast/* itheima/`是将itcast目录下所有文件复制到itheima目录下

`mv`为文件或目录重命名，也可以将文件或目录进行移动，语法：`mv source dest`

**案例：**  `mv hello.txt hi.txt`是将hello.txt改名为hi.txt，`mv hi.txt itheima/`是将文件hi.txt移动到itheima目录中，`mv hi.txt itheima/hello.txt`是将hi.txt移动到itheima目录中并改名为itheima，`mv itcast/ itheima/`是当itheima目录不存在，将itcast目录改名为itheima，`mv itcast/ itheima/`是当itheima目录存在，将itcast目录移动到itheima目录中

### [](#打包压缩命令 "打包压缩命令")打包压缩命令

`tar`对文件进行打包、解包、压缩或解压缩，语法：`tar [-zcxvf] fileName [files]`

**说明：**  包文件名缀为.tar表示只是完成了打包，并没有压缩；包文件后缀为.tar.gz表示完成了打包还进行了压缩

**参数选项：** 

*   -z：z代表的是gzip，通过gzip命令处理文件，gzip可以对文件压缩或解压
*   -c：c代表的是create，即创建新的包文件
*   -x：x代表的是extract，实现从包文件中还原文件
*   -v：v代表的是verbose，显示命令的执行过程
*   -f：f代表的是file，用于指定包文件的名称

**案例：** `tar -zxvf hello.tar.gz`将hello.tar.gz文件进行解压并将解压后的文件放在当前目录， `tar -zxvf hello.tar.gz -C /usr/local`将hello.tar.gz文件进行解压并将解压后的文件放在/usr/local目录下

### [](#文本编辑命令 "文本编辑命令")文本编辑命令

`vi`是Linux命令提供的一个文本编辑工具，可以对文件内容进行编辑，类似于Windows记事本，语法：`vi fileName`

`vim`是从vi发展来的一个功能更加强大的文本编辑工具，在编辑文件时可以对文件内容进行着色，方便对文件进行编辑处理，所以实际中vim更加常用，而要使用vim命令则需要安装：`yum install vim`

`vim`对文件内容进行编辑，语法：`vim fileName`

**说明：**  在使用vim命令编辑文件时，如果指定的文件存在则直接打开此文件，如果指定的文件不存在则新建文件；vim进行文本编辑时共分为三种模式，分别是命令行模式、插入模式和底行模式，这三种模式可以互相切换，在使用vim时一定要注意当前所处模式

**命令模式**

*   通过vim命令打开文件后默认进入命令模式，另外两种模式需要首先进入命令模式才能进入彼此
*   命令模式下可以查看文件内容、移动光标（上下左右箭头、gg、G）

**插入模式**

*   插入模式下可以对文件内容进行编辑
*   在命令模式下按下\[i,a,o\]任意一个，可以进入插入模式，进入插入模式后，下方会出现【insert】字样
*   在插入模式下按下ESC键即可回到命令模式

**底行模式**

*   底行模式下可以通过命令对文件内容进行查找、显示行号、退出等操作
*   在命令模式下按下\[:,/\]任意一个就可进入底行模式
*   通过/方式进入底行模式后，可以对文件内容进行查找
*   通过:方式进入底行模式后，可以输入wq（保存并退出）、q!（不保存退出）、set nu（显示行号）

### [](#查找命令 "查找命令")查找命令

`find`在指定目录下查找文件，语法：`find dirName -option fileName`

**案例：**  `find . -name "*.java"`即在当前目录及其子目录下查找.java结尾文件，`find /itcast -name "*.java"`在/itcast目录及其子目录下查找.java结尾的文件

`grep`从指定文件中查找指定的文件内容，语法：`gerp content fileName`

**案例：**  `grep Hello HelloWorld.java`即查找HelloWorld.java文件中出现的Hello字符串的位置，`grep hello *.java`即查找当前目录中所有.java结尾的文件中包含hello字符串的位置

[](#六、软件安装 "六、软件安装")六、软件安装
--------------------------

*   软件安装方式
*   安装jdk
*   安装Tomcat
*   安装MySQL
*   安装lrzsz

### [](#软件安装方式 "软件安装方式")软件安装方式

**二进制发布包安装：**  软件已经针对具体平台编译打包发布，只要解压，修改配置即可

**rpm安装：**  软件已经按照redhat的包管理规范进行打包，使用rpm命令进行安装，不能自行解决库依赖问题

**yum安装：**  一种在线软件安装方式，本质上还是rpm安装，会自动下载安装包并安装，安装过程中自动解决库依赖问题

**源码编译安装：**  软件以源码工程的形式发布，需要自己编译打包

### [](#安装jdk "安装jdk")安装jdk

**第一步** 从[HUAWEI镜像源](https://repo.huaweicloud.com/java/jdk)下载Linux版JDK安装包

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722200024421.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722200024421.png)

**第二步** 使用FinalShell自带的上传功能将jdk的二进制发布包上传到Linux

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722200944039.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722200944039.png)

**第三步** 解压安装包，命令为`tar -zxvf jdk-8u171-linux-x64.tar.gz -C /usr/local`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722201903688.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722201903688.png)

**第四步** 配置环境变量，使用vim命令修改/etc/profile文件，在文件末尾添加如下配置

```plaintext
JAVA_HOME=/usr/local/jdk1.8.0_171
PATH=$JAVA_HOME/bin:$PATH
```

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722202606590.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722202606590.png)

**第五步** 重新加载profile文件，使更改的配置立即生效，命令：`source /etc/profile`；检查安装是否成功，命令：`java -version`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722202750491.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722202750491.png)

### [](#安装Tomcat "安装Tomcat")安装Tomcat

**第一步** 从[官方网站](https://tomcat.apache.org/download-80.cgi)下载Tomcat二进制发布包

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722203613052.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722203613052.png)

**第二步** 使用FinalShell自带的上传工具将Tomcat的二进制发布包上传到Linux

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722204945129.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722204945129.png)

**第三步** 解压安装包，命令为`tar -zxvf apache-tomcat-8.5.91.tar.gz -C /usr/local`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205136431.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205136431.png)

**第四步** 进入Tomcat的bin目录启动服务，命令为`sh startup.sh`或`./startup.sh`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205422438.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205422438.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205602577.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722205602577.png)

#### [](#验证Tomcat启动 "验证Tomcat启动")验证Tomcat启动

**查看启动日志**

`more /usr/local/apache-tomcat-8.5.91/logs/catalina.out`

`tail -50 /usr/local/apache-tomcat-8.5.91/logs/catalina.out`

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210219464.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210219464.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210300100.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210300100.png)

**查看进程**

`ps -ef|grep tomcat`

*   ps命令是Linux下非常强大的进程查看命令，通过ps -ef可以查看当前运行的所有进程的详细信息
*   ”|“在Linux中称为管道符，可以将前一个命令的结果输出给后一个命令作为输入
*   使用ps命令查看进程时，经常配合管道符和查找命令grep一起使用，来查看特定进程

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210847479.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722210847479.png)

在本地机上测试连接Linux上的tomcat服务器，会发现连接失败

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211120084.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211120084.png)

#### [](#防火墙操作 "防火墙操作")防火墙操作

*   查看防火墙状态：`systemctl status firewalld`或`firewall-cmd --state`
*   暂时关闭防火墙：`systemctl stop firewalld`
*   永久关闭防火墙：`systemctl disable firewalld`
*   开启防火墙：`systemctl start firewalld`
*   开发指定端口：`firewall-cmd --zone=public --add-port=8080/tcp --permanent`
*   关闭指定端口：`firewall-cmd --zone=public --remove-port=8080/tcp --permanent`
*   立即生效：`firewall-cmd --reload`
*   查看开放的端口：`firewall-cmd --zone=public --list-ports`

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211840689.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211840689.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211851853.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722211851853.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722212313150.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722212313150.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722212325381.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722212325381.png)

**注意：**  systemctl是管理Linux中服务的命令，可对服务进行启动、停止、重启、查看状态等操作；firewall-cmd是Linux中专门用于控制防火墙的命令；为了保证系统安全，服务器的防火墙不建议关闭

#### [](#关闭Tomcat服务 "关闭Tomcat服务")关闭Tomcat服务

**第一种**

运行Tomcat下的bin目录中提供停止服务的脚本文件shutdown.sh，命令：`sh shutdown.sh`或`./shutdown.sh`

**第二种**

查看Tomcat进程，获得进程id，然后执行结束进程的命令：`kill -9 进程号`

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722213508170.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722213508170.png)

### [](#安装MySQL "安装MySQL")安装MySQL

先检测当前系统中是否已安装MySQL数据库，如果已安装，那么在安装则会失败，同时CentOS7自带的mariadb会与MySQL数据库冲突

`rpm -qa`：查询当前系统中安装的所有软件

`rpm -qa|grep mysql`：查询当前系统中安装的软件名称中是否有mysql

`rpm -qa|grep mariadb`：查询当前系统中安装的软件名称中是否有mariadb

RPM（Red-Hat Package Manager）是软件包管理器，是红帽Linux用于管理和安装软件的工具

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722214231594.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722214231594.png)

卸载已安装的冲突软件

`rpm -e --nodeps 软件名称`：卸载软件

`rpm -e --nodeps mariadb-libs-5.5.68-1.el7.x86_64`

【实践图】

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722214708954.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722214708954.png)

到这里准备工作完成了，接下来就是正式安装

**第一步** 到[官网](https://downloads.mysql.com/archives/community)下载Linux版MySQL，这里选择MySQL的版本和本地机相同

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722215310980.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722215310980.png)

**第二步** 使用FinalShell自带的上传工具将MySQL压缩包上传到Linux

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722215829742.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722215829742.png)

**第三步** 移动mysql压缩包到创建的目录下

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722220105983.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722220105983.png)

**第四步** 解压mysql压缩包

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722220429858.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722220429858.png)

**第五步** 安装rpm软件包

`rpm -ivh *.rpm --nodeps --force`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722221603126.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722221603126.png)

**第六步** 启动mysql

`systemctl status mysqld`：查看mysql服务状态

`systemctl start mysqld`：启动mysql服务

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222026605.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222026605.png)

**说明：**  可以设置开机时启动mysql服务，避免每次开机启动mysql

`systemctl enable mysqld`：开机启动mysql服务

`netstat -tunlp`：查看已启动的服务

`netstat -tunlp|grep mysql`

`ps -ef|grep mysql`：查看mysql进程

**注意：**  需要安装net-tools

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222408872.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222408872.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222614009.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722222614009.png)

#### [](#登录MySQL数据库 "登录MySQL数据库")登录MySQL数据库

查阅临时密码

`cat /var/log/mysqld.log`：查看文件内容

`cat /var/log/mysqld.log|grep password`：查看文件内容中包含password的行信息

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722223333466.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722223333466.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722223624852.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722223624852.png)

**修改临时密码**

先修改密码在设置校验规则与密码长度

`alter user 'root'@'localhost' identified with mysql_native_password by 'Root_12root';`：修改的密码中必须有数字、大小写字母和特殊字符且长度在8以上

`set global validate_password.policy=0;`：设置密码安全等级低，便于密码修改

`set global validate_password.length=4;`：设置密码长度最低位数

`ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';`：修改密码为简单密码

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722225828959.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722225828959.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722225859441.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722225859441.png)

**开启访问权限**

先创建用户，在对该用户分配用户权限，然后在刷新权限

`CREATE USER 'root'@'%' IDENTIFIED BY '123456';`

`GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;`

`FLUSH PRIVILEGES;`

**注意：**  `CREATE USER 'root'@'%' IDENTIFIED BY '123456';`中`'123456'`为远程连接的访问密码

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101038751.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101038751.png)

开放3306端口：`firewall-cmd --zone=public --add-port=3306/tcp --permanent`、`firewall-cmd --reload`、`firewall-cmd --zone=public --list-ports`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722231453261.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230722231453261.png)

使用navicat测试远程连接Linux上的mysql，也可以使用DataGrip测试远程连接Linux上的mysql

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101742200.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101742200.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101801312.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723101801312.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723110728145.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723110728145.png)

### [](#安装lrzsz "安装lrzsz")安装lrzsz

使用Yum安装

> Yum（全称为Yellow dog Updater,Modified）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动出来依赖关系，并且一次安装所有依赖的软件包，无序繁琐地一次次下载、安装

搜索lrzsz安装包，命令：`yum list lrzsz`，然后使用yum命令在线安装，命令：`yum install lrzsz.x86_64`

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723102656892.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723102656892.png)

[![](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723102822687.png)
](https://mk-image-article.oss-cn-hangzhou.aliyuncs.com/img/image-20230723102822687.png)