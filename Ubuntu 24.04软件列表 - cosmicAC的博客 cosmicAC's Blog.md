# Ubuntu 24.04软件列表 - cosmicAC的博客 | cosmicAC's Blog
       Ubuntu 24.04软件列表 - cosmicAC的博客 | cosmicAC's Blog                        


Ubuntu 24.04软件列表
================

Posted by wyj on December 3, 2018 / Edited on August 30, 2024

具体指Ubuntu 24.04中我装了的软件。粗体字是使用频率很高或者特别重要的。绿色字是新加的。

程序开发环境[](#程序开发环境)
=================

*   **gedit：写代码、打草稿、记录备忘事项、~及看小说~的万能应用**
    *   **gedit-plugins：强大的插件**
    *   gedit-source-code-browser-plugin：让gedit像是IDE的方法
    *   markdown-preview：markdown预览
*   **vim-gtk3：待在终端里懒得出来了**
*   **git：版本控制工具**
*   **clang-14：c编译器**
*   **gcc-13：另一个c编译器**
*   **python3：python3.12，逼我去用venv，太麻烦了**
    *   **sympy：像mathematica一样的几乎万能的数学计算工具**
    *   **numpy：比c++快多了的数学计算**
    *   **ipython：像mathematica一样有丰富功能的python命令行**
    *   **matplotlib：像mathematica一样的画图工具**
    *   **pip3：安装模块**
    *   jupyter：相当于ipython的图形界面
    *   pypy3：运行速度飞快的python3替代品
    *   elasticsearch：用于脚本
    *   pypinyin：拼音
    *   torch：为什么pytorch现在这么流行啊
    *   youtube-dl：下载YouTube视频（其实是用来听歌）
    *   cvxpy：各种优化的Solver
    *   h5py：读取HDF5数据集
    *   bpy：读取Blender对象进行计算
*   default-jre：Java运行时
*   nodejs：本地跑js用
*   fpc：历史遗留问题
*   qtcreator：C++图形界面解决方案
*   VS Code：功能很多的代码编辑器，插件很多，很方便，足够智能
*   lemonlime：lemon的升级版，OI评测使用
*   g++-mingw-w64-x86-64：到Win64的交叉编译

工具[](#工具)
=========

#### 文本处理类型[](#文本处理类型)

*   **typora：强大的markdown编辑器，Linux可以免费无限期试用正版**
*   **搜狗输入法：适配了22.04的搜狗输入法，挺好用的**
*   **TeXstudio：TeX**
*   Calibre：epub阅读器
*   wps：比libreoffice好用
*   net.cnki.cajviewer：垃圾知网的垃圾caj格式阅读器
*   astyle：就是Dev-C++中的astyle，代码格式化
*   fcitx-libpinyin：（备用的）拼音输入法
*   mozc：日语输入法

#### GUI优化[](#gui优化)

*   dconf-editor：类似于windows的注册表编辑器
*   gnome-tweaks：gnome shell高级设置
*   gnome-shell-extensions：有用的插件
    *   Dash to Panel：高度可定制的Dash（~一听就是空洞骑士、ori和蔚蓝里很需要的~）
    *   TopiconsFix：把QQ音乐和TIM的后台图标移动到右上，从而去掉恼人的小窗口
    *   GS Connect：配合 KDE Connect的App连接Android手机，很实用
    *   bing-wallpaper-changer：选择每天的Bing壁纸作为桌面，每日以及开机时自动更换成最新的壁纸
    *   [Bluetooth Battery Meter](https://extensions.gnome.org/extension/6670/bluetooth-battery-meter/)：显示蓝牙连接设备的电量

#### 其他工具[](#其他工具)

*   **QQ：现在有Linux版啦，非常好用**
*   **weixin：来自openkylin的Linux版**
*   Jekyll：本地跑博客用
*   locate：超级好用的飞速的文件搜索
*   virtualbox：虚拟机
    *   Ubuntu 24.04：Ubuntu 24.04
    *   Windows 10：Windows 10
*   腾讯会议：腾讯会议，对没错这东西有Linux版了，而且新版本把杂音很吵的bug给修好了
*   Shotcut：视频剪辑软件
*   Mathematica：Mathematica（盗版的）
*   MATLAB：付费版numpy+matplotlib
*   ubuntu-restricted-extras：播放mp3、mp4、解压RAR使用
*   kolourpaint：ubuntu画图
*   vlc：KDE的视频播放器，比默认的好很多
*   Zoom：Zoom
*   ries：反符号计算器
*   adb：连接手机和Anbox
*   gparted：硬盘分区神器，装系统必备
*   WoeUSB：我唯一会的做Windows安装盘方法
*   emsdk：做WebAssembly试验后留下来的
*   pix2tex：Latex OCR 工具
*   fzf：终端里查找文件用的，还不太会用
*   Blender：科研用的，我可不懂艺术

网络[](#网络)
=========

*   **chrome：浏览器**
    *   **AdBlock Plus：广告拦截**
    *   **SwitchyOmega：选择性代理控制**
    *   **沙拉查词：划词翻译**
    *   TamperMonkey：运行用户脚本
        *   洛谷用户名优化：变成管理员
        *   网页限制解除：复制网页内容
        *   百度文库免费下载
        *   Tenhou-Pairi Kokei display：天凤牌理显示好型率
        *   NAGA\_ANALYZE：雀魂牌谱转NAGA，一定要小号用，封号风险高
        *   [tsinghua-ereserves-lib-downloader](https://github.com/A1phaN/tsinghua-ereserves-lib-downloader)：下载教材PDF版本
    *   setupVPN：救急用的VPN
    *   HoXX VPN：setupVPN的等价可选替代
    *   百度网盘助手：下载百度网盘文件，已失效
    *   谷歌访问助手：翻墙用的基本跳板
    *   Gnome shell integration：安装gnome插件用
    *   Requestly：重定向网址（超级好用），运行自定义的JS（这个功能暂时还没用到）
    *   FireShot：网页截图工具，可以截取网页的特定部分和制作长截图
    *   Bypass Paywalls：免费浏览各种新闻网站
    *   [Lyrics for Spotify](https://github.com/mantou132/Spotify-Lyrics)：免费看Spotify歌词
*   **Clash for Windows：但是Linux能用；统一管理各种代理**
*   Tor Browser：Tor浏览器
*   electron-ssr：曾经最常用的科学上网软件
*   [GoAuthing](https://github.com/z4yx/GoAuthing)：连接清华WiFi无需认证
*   chrome-gnome-shell：安装gnome插件用
*   whois：查IP用
*   curl：超级好用的网络工具
*   aria2：高速下载各种文件
*   tsocks：用socks代理加速wget、git等等程序
*   百度网盘：功能有限的linux百度网盘
*   openssh-server：ssh服务器
*   telegram-desktop：telegram的图形界面客户端
*   wireshark：用来抓包，挺有意思的
*   aircrack-ng：用来在monitor mode下抓包
*   openconnect：连接清华VPN用

娱乐[](#娱乐)
=========

*   **洛雪音乐助手：什么歌都有的播放器，本人是contributor之一**
*   **steam：Steam**
    *   Ori1：终极版，需要在杉果上买，比二代更platformer一点
    *   暗黑地牢2：不太耐玩，越改越烂
    *   Turing Complete：有趣的数字电路设计游戏，但是体量小，有点贵
    *   Ori2：唯美而有趣的类银河恶魔城游戏，与空洞骑士很像
    *   以撒：Repentance
    *   空洞骑士：随机mod真好玩，还有Glimmering Realm等mod
    *   蔚蓝：令人抑郁的Celeste，但是有Into the Jungle、春游、草莓酱等有趣而高质量的mod
    *   暗黑地牢：现在DLC也买了
    *   雀魂：沉迷麻将不可自拔
*   wine和wine64：运行游戏等Windows程序
    *   Win7Games4Win10：红心大战等等游戏（也是盗版的）
    *   ShogiDokoro：将棋
    *   以撒：盗版的
        *   Afterbirth+
        *   Antibirth
        *   Wrath of the Lamb Eternal Edition
*   bash-insulter：纠正你的错误命令，这里指的是我自己魔改了的版本，加入了编程随想的名言
*   sl：纠正你的错误ls命令
*   cowsay：有趣的图片，可以用来显示snzakioi
*   gnome-2048：本地2048
*   kapman：吃豆人
*   asciiquarium：终端水族馆
*   apt-build：装了好玩
*   screenfetch：装了好玩
*   anbox：运行android应用程序
*   OBS Studio：直播软件，我用来录视频
*   stellarium：看星星
*   网易云音乐：网易云音乐，~啥歌都听不了~

* * *

Copyright © cosmicAC's Blog 2024  
Theme on [GitHub](https://github.com/2o181o28/2o181o28.github.io.git) |
