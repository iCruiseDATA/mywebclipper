# 2025-02-19-VPS Init（VPS 初始化配置）
修改时区
----

bash ▽

`ln -sf /usr/share/zoneinfo/Etc/GMT-8 /etc/localtime` 

配置bash命令
--------

bash ▽

`alias l='ls -Al --color=auto' alias ll='ls -Alh --color=auto'` 

配置apt源
------

删除普通用户
------

安装工具
----

bash ▽

`apt update apt install -y systemd-timesyncd vim curl wget gcc g++ git make screen telnet jq bc tcptrack` 

修改主机名
-----

bash ▽

`vim /etc/hosts vim /etc/hostname` 

配置ssh key
---------

bash ▽

`mkdir .ssh chmod 600 .ssh   vim .ssh/authorized_keys chmod 600 .ssh/authorized_keys` 

配置sshd
------

bash ▽

`vim /etc/ssh/sshd_config   PermitRootLogin prohibit-password PubkeyAuthentication yes PasswordAuthentication no ClientAliveInterval 15 ClientAliveCountMax 3` 

更改密码
----

配置git
-----

bash ▽

`git config --global user.name "Akvicor" git config --global user.email akvicor@kayuki.org git config --global core.editor vim` 

motd脚本
------

bash ▽

`vim /etc/motd vim /etc/update-motd.d/99-custom chmod +x /etc/update-motd.d/99-custom` 

内容

bash ▽

`#!/bin/bash   # 主机名 HOSTNAME=$(cat /etc/hostname)   # 获取系统运行时间（天数） UPTIME_DAYS=$(awk '{print int($1/86400)}' /proc/uptime)   # 获取系统时间 DATE=$(date)   # 获取IPv4地址 IPV4=$(curl -s --max-time 2 ip.sb -4 || echo "-")   # 获取IPv6地址 IPV6=$(curl -s --max-time 2 ip.sb -6 || echo "-")   # 架构 CPU_ARCH=$(lscpu | grep "^Architecture:" | awk '{print substr($0, index($0, $2))}')   # CPU名称 CPU_NAME=$(lscpu | grep "^Model name:" | awk '{print substr($0, index($0, $3))}') CPU_BIOS_NAME=$(lscpu | grep "^BIOS Model name:" | awk '{print substr($0, index($0, $4))}')   # CPU数量 #CPU_NUM=$(cat /proc/cpuinfo| grep "processor"| wc -l) CPU_NUM=$(lscpu | grep "^CPU(s):" | awk '{print substr($0, index($0, $2))}')   # CPU Socket数量 CPU_SOCKET=$(lscpu | grep "^Socket(s):" | awk '{print substr($0, index($0, $2))}')   # CPU Core per Socket数量 CPU_CORE_PER_SOCKET=$(lscpu | grep "^Core(s) per socket:" | awk '{print substr($0, index($0, $4))}')   # CPU Thread per Core数量 CPU_THREAD_PER_CORE=$(lscpu | grep "^Thread(s) per core:" | awk '{print substr($0, index($0, $4))}')   # CPU最小频率 CPU_MIN_Hz=$(lscpu | grep "^CPU min MHz:" | awk '{print substr($0, index($0, $4))}' | awk '{printf "%.2f",$0/1000}')   # CPU最大频率 CPU_MAX_Hz=$(lscpu | grep "^CPU max MHz:" | awk '{print substr($0, index($0, $4))}' | awk '{printf "%.2f",$0/1000}')   # 获取内存占用 MEM_USAGE=$(free -m | sed -n '2p' | awk '{printf "%.2fG / %.2fG\n",$3/1024,$2/1024}')   # 获取硬盘使用情况 DISK_USAGE=$(df -h / | awk 'NR==2 {print $3 " / " $2}')     echo "-----------------------------------------" echo "  Hostname: $HOSTNAME" echo "  Online: $UPTIME_DAYS days" echo "  Date: $DATE" echo "  Network: $IPV4 / $IPV6" echo "  CPU Arch: ${CPU_ARCH}" echo "  CPU Name: ${CPU_NAME}" echo "  CPU BName: ${CPU_BIOS_NAME}" echo "  CPU Num: ${CPU_NUM}T (${CPU_SOCKET}S*${CPU_CORE_PER_SOCKET}C*${CPU_THREAD_PER_CORE}T)" echo "  CPU Hz: ${CPU_MIN_Hz}GHz / ${CPU_MAX_Hz}GHz" echo "  Memory: $MEM_USAGE" echo "  Disk: $DISK_USAGE" echo "-----------------------------------------"` 

安装Caddy
-------

bash ▽

`apt install -y debian-keyring debian-archive-keyring apt-transport-https curl curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/gpg.key' | gpg --dearmor -o /usr/share/keyrings/caddy-stable-archive-keyring.gpg curl -1sLf 'https://dl.cloudsmith.io/public/caddy/stable/debian.deb.txt' | tee /etc/apt/sources.list.d/caddy-stable.list apt update apt install caddy` 

安装Docker
--------

bash ▽

`apt-get update apt-get install ca-certificates curl install -m 0755 -d /etc/apt/keyrings curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc chmod a+r /etc/apt/keyrings/docker.asc echo \  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian \ $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \ tee /etc/apt/sources.list.d/docker.list > /dev/null apt-get update apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin`