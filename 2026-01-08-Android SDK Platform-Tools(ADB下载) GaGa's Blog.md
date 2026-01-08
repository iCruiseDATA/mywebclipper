# 2026-01-08-Android SDK Platform-Tools(ADB下载) | GaGa's Blog
                             Android SDK Platform-Tools(ADB下载) | GaGa's Blog 

[

GaGa's Blog

](/)

One GaGa, One World !

*   [Home](/)
*   [Archives](/archives/)
*   [Tags](/tags/)
*   [Sitemap](/sitemap.xml)
*   [friends](/friends/)
*   [About](/about/)
*   Search

*   Table of Contents
*   Overview

1.  [1. 1.下载地址（官方）](#1-%E4%B8%8B%E8%BD%BD%E5%9C%B0%E5%9D%80%EF%BC%88%E5%AE%98%E6%96%B9%EF%BC%89)
2.  [2. 2.安装步骤](#2-%E5%AE%89%E8%A3%85%E6%AD%A5%E9%AA%A4)
    1.  [2.1. 2.1. 解压](#2-1-%E8%A7%A3%E5%8E%8B)
    2.  [2.2. 2.2. 配置环境变量（方便全局使用 adb）](#2-2-%E9%85%8D%E7%BD%AE%E7%8E%AF%E5%A2%83%E5%8F%98%E9%87%8F%EF%BC%88%E6%96%B9%E4%BE%BF%E5%85%A8%E5%B1%80%E4%BD%BF%E7%94%A8-adb%EF%BC%89)
    3.  [2.3. 2.3. 验证安装](#2-3-%E9%AA%8C%E8%AF%81%E5%AE%89%E8%A3%85)
3.  [3. 3.adb命令参数](#3-adb%E5%91%BD%E4%BB%A4%E5%8F%82%E6%95%B0)
    1.  [3.1. 3.1.adb 基本命令](#3-1-adb-%E5%9F%BA%E6%9C%AC%E5%91%BD%E4%BB%A4)
    2.  [3.2. 3.2.设备连接相关](#3-2-%E8%AE%BE%E5%A4%87%E8%BF%9E%E6%8E%A5%E7%9B%B8%E5%85%B3)
    3.  [3.3. 3.3.应用管理](#3-3-%E5%BA%94%E7%94%A8%E7%AE%A1%E7%90%86)
    4.  [3.4. 3.4.文件操作](#3-4-%E6%96%87%E4%BB%B6%E6%93%8D%E4%BD%9C)
    5.  [3.5. 3.5.调试 & Shell](#3-5-%E8%B0%83%E8%AF%95-amp-Shell)
    6.  [3.6. 3.6.设备控制](#3-6-%E8%AE%BE%E5%A4%87%E6%8E%A7%E5%88%B6)
    7.  [3.7. 3.7.端口转发 & 调试](#3-7-%E7%AB%AF%E5%8F%A3%E8%BD%AC%E5%8F%91-amp-%E8%B0%83%E8%AF%95)
    8.  [3.8. 3.8. 常用组合示例](#3-8-%E5%B8%B8%E7%94%A8%E7%BB%84%E5%90%88%E7%A4%BA%E4%BE%8B)
4.  [4. Reference](#Reference)



Focus on operation and maintenance related work: sre、devops、kubernetes、cicd、system、security、troubleshooting

[1178 posts](/archives/)

[577 tags](/tags/)

[GitHub](https://github.com/mvpbang "GitHub → https://github.com/mvpbang") [E-Mail](mailto:mvpbang@163.com "E-Mail → mailto:mvpbang@163.com") [Issues](https://github.com/mvpbang/mvpbang.github.io/issues "Issues → https://github.com/mvpbang/mvpbang.github.io/issues") [Rss](/atom.xml "Rss → /atom.xml")

[![](https://cdnjs.cloudflare.com/ajax/libs/creativecommons-vocabulary/2020.11.3/assets/license_badges/small/by_nc_sa.svg)
](https://creativecommons.org/licenses/by-nc-sa/4.0/)

          

Android SDK Platform-Tools(ADB下载)
=================================

Posted on 2025-09-06 Views: 1522

**Android SDK Platform-Tools**（ADB、fastboot 等工具），最简单的方式是直接从 Google 官方下载对应平台的压缩包，解压即可使用，不需要额外安装 Android Studio。

* * *

[](#1-下载地址（官方） "1.下载地址（官方）")1.下载地址（官方）
--------------------------------------

*   [https://developer.android.com/tools/releases/platform-tools?hl=zh-cn](https://developer.android.com/tools/releases/platform-tools?hl=zh-cn)

*   **Windows**: [platform-tools-latest-windows.zip](https://developer.android.com/studio/releases/platform-tools)
*   **macOS**: [platform-tools-latest-darwin.zip](https://developer.android.com/studio/releases/platform-tools)
*   **Linux**: [platform-tools-latest-linux.zip](https://developer.android.com/studio/releases/platform-tools)

> 建议从 [Google 官方下载页面](https://developer.android.com/studio/releases/platform-tools) 获取，以保证是最新版本。

*   window
    *   [https://dl.google.com/android/repository/platform-tools-latest-windows.zip](https://dl.google.com/android/repository/platform-tools-latest-windows.zip)
*   macos
    *   [https://dl.google.com/android/repository/platform-tools-latest-darwin.zip](https://dl.google.com/android/repository/platform-tools-latest-darwin.zip)
*   linux
    *   [https://dl.google.com/android/repository/platform-tools-latest-linux.zip](https://dl.google.com/android/repository/platform-tools-latest-linux.zip)

* * *

[](#2-安装步骤 "2.安装步骤")2.安装步骤
--------------------------

### [](#2-1-解压 "2.1. 解压")2.1. 解压

把下载好的压缩包解压到一个目录，例如：

*   Windows: `C:\platform-tools`
*   macOS/Linux: `~/platform-tools`

### [](#2-2-配置环境变量（方便全局使用-adb） "2.2. 配置环境变量（方便全局使用 adb）")2.2. 配置环境变量（方便全局使用 `adb`）

*   **Windows**
    
    1.  右键 “此电脑” → 属性 → 高级系统设置 → 环境变量
    2.  在系统变量里找到 `Path` → 编辑 → 添加 `C:\platform-tools`
    3.  确认并重启命令行
*   **macOS/Linux**  
    编辑 `~/.bashrc` 或 `~/.zshrc`，加上：
    
    ```bash
    export PATH=$PATH:$HOME/platform-tools
    ```
    
    然后执行 `source ~/.bashrc` 或 `source ~/.zshrc`
    

### [](#2-3-验证安装 "2.3. 验证安装")2.3. 验证安装

连接好设备（记得在手机里打开 **开发者选项 → USB调试**），执行：

```bash
adb version
adb devices
```

如果能看到版本号和设备列表，就说明安装成功。

[![](https://blog.mvpbang.com/resource/0e6a35d30ace4eb79d2b6c719b496432.png)
](https://blog.mvpbang.com/resource/0e6a35d30ace4eb79d2b6c719b496432.png "6f11168173d78c30b147f89d2595feef.png")

[](#3-adb命令参数 "3.adb命令参数")3.adb命令参数
-----------------------------------

### [](#3-1-adb-基本命令 "3.1.adb 基本命令")3.1.adb 基本命令

| 命令 | 说明 |
| --- | --- |
| `adb devices` | 列出已连接的设备 |
| `adb version` | 查看 adb 版本 |
| `adb kill-server` | 停止 adb 服务 |
| `adb start-server` | 启动 adb 服务 |
| `adb reconnect` | 重新连接所有设备 |

* * *

### [](#3-2-设备连接相关 "3.2.设备连接相关")3.2.设备连接相关

| 命令 | 说明 |
| --- | --- |
| `adb connect <ip>:<port>` | 通过 TCP/IP 连接设备（如 `adb connect 192.168.1.100:5555`） |
| `adb disconnect <ip>:<port>` | 断开网络设备连接 |
| `adb -s <serial>` | 指定设备执行命令（多设备时必须用） |

* * *

### [](#3-3-应用管理 "3.3.应用管理")3.3.应用管理

| 命令 | 说明 |
| --- | --- |
| `adb install app.apk` | 安装 APK |
| `adb install -r app.apk` | 重新安装（保留数据） |
| `adb install -d app.apk` | 允许降级安装 |
| `adb install -g app.apk` | 安装并自动授予权限 |
| `adb uninstall <包名>` | 卸载应用 |
| `adb uninstall -k <包名>` | 卸载但保留数据和缓存 |

* * *

### [](#3-4-文件操作 "3.4.文件操作")3.4.文件操作

| 命令 | 说明 |
| --- | --- |
| `adb push <本地文件> <设备路径>` | 复制文件到设备 |
| `adb pull <设备文件> <本地路径>` | 从设备复制文件 |
| `adb shell ls /sdcard/` | 列出设备文件目录 |

* * *

### [](#3-5-调试-amp-Shell "3.5.调试 & Shell")3.5.调试 & Shell

| 命令 | 说明 |
| --- | --- |
| `adb shell` | 进入设备 shell |
| `adb shell <命令>` | 执行单条命令，例如 `adb shell ls /sdcard/` |
| `adb logcat` | 查看系统日志 |
| `adb logcat -s <tag>` | 查看指定 tag 日志 |
| `adb bugreport` | 导出完整系统调试报告 |

* * *

### [](#3-6-设备控制 "3.6.设备控制")3.6.设备控制

| 命令 | 说明 |
| --- | --- |
| `adb reboot` | 重启设备 |
| `adb reboot bootloader` | 重启到 bootloader |
| `adb reboot recovery` | 重启到 recovery |
| `adb root` | 以 root 模式重启 adb（设备需支持） |
| `adb remount` | 重新挂载系统分区为可写（需 root） |
| `adb tcpip 5555` | 开启 adb TCP/IP 连接模式，端口 5555 |

* * *

### [](#3-7-端口转发-amp-调试 "3.7.端口转发 & 调试")3.7.端口转发 & 调试

| 命令 | 说明 |
| --- | --- |
| `adb forward tcp:<本地端口> tcp:<设备端口>` | 本地端口转发到设备 |
| `adb reverse tcp:<设备端口> tcp:<本地端口>` | 设备端口转发到本地 |
| `adb shell am start -n <包名>/<Activity>` | 启动应用 |
| `adb shell pm list packages` | 列出所有安装的包 |
| `adb shell pm clear <包名>` | 清除应用数据 |

* * *

### [](#3-8-常用组合示例 "3.8. 常用组合示例")3.8. 常用组合示例

```bash
1.adb服务
adb  start-server  # 启动adb服务
adb -P 5555 start-server # 启动adb服务指定端口
adb kill-server # 停止adb服务

2.连接
adb connect ip:port
adb devices                   # 查看设备
adb disconnect ip:port  # 端口特定设备
adb disconnect  # 断开所有连接

3.安装/使用
adb install -r app.apk        # 安装或更新 APK
adb push config.json /sdcard/ # 复制文件到设备
adb shell pm list packages    # 查看安装的包
adb logcat | grep Activity    # 过滤日志
adb tcpip 5555                # 开启无线调试
adb connect 192.168.1.100:5555 # 连接设备
```

[](#Reference "Reference")Reference
-----------------------------------
*   **Post author:** GaGa
*   **Post link:** [https://blog.mvpbang.com/p/764de852955c4d52b5fd744e53605c7b/](https://blog.mvpbang.com/p/764de852955c4d52b5fd744e53605c7b/ "Android SDK Platform-Tools(ADB下载)")
*   **Copyright Notice:** All articles in this blog are licensed under [BY-NC-SA](https://creativecommons.org/licenses/by-nc-sa/4.0/) unless stating additionally.

[\# download](/tags/download/) [\# adb](/tags/adb/) [\# android](/tags/android/)

[chpasswd在Linux系统中用于批量更改用户密码](/p/d6e066f105ce438386299974007f1afc/ "chpasswd在Linux系统中用于批量更改用户密码")

[sshd隧道模式L/R/D](/p/c65294239ae84e40879b488071e03497/ "sshd隧道模式L/R/D")

© 2024 – 2026 Copyright © GaGa. All Rights Reserved.

45028 56558

Powered by [Hexo](https://hexo.io/) & [NexT.Muse](https://theme-next.js.org/muse/)

89%

[](https://github.com/mvpbang "Follow me on GitHub")