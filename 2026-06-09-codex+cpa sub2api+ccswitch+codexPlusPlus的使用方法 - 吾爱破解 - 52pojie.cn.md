# 2026-06-09-codex+cpa/sub2api+ccswitch+codexPlusPlus的使用方法 - 吾爱破解 - 52pojie.cn
给新手小白（包括我自己）简单介绍一下最近这些热门软件的使用方法。

cpa：

*   全称是 CLIProxyAPI
*   项目地址：[https://github.com/router-for-me/CLIProxyAPI](https://github.com/router-for-me/CLIProxyAPI)
*   作用：登录你的 chatgpt 用于使用，可以同时加载多个账号，推荐电脑本地使用。

sub2api:

*   项目地址：[https://github.com/Wei-Shaw/sub2api](https://github.com/Wei-Shaw/sub2api)
*   作用：登录你的 chatgpt 用于使用，可以同时加载多个账号，推荐服务器使用。

cc-switch:

*   项目地址：[https://github.com/farion1231/cc-switch](https://github.com/farion1231/cc-switch)
*   作用：可以一键管理切换各种供应商，内有各种供应商的设置模板，对新手小白友好。

codex++：

*   项目地址：[https://github.com/BigPizzaV3/CodexPlusPlus](https://github.com/BigPizzaV3/CodexPlusPlus)
*   作用：codex 的增强插件，解锁了 codex 的一些内容。

coedx：

*   window 下载地址：[https://apps.microsoft.com/detail/9PLM9XGG6VKS?hl=neutral&gl=CN&ocid=pdpshare](https://apps.microsoft.com/detail/9PLM9XGG6VKS?hl=neutral&gl=CN&ocid=pdpshare)
*   mac 下载地址：[https://persistent.oaistatic.com/codex-app-prod/Codex.dmg](https://persistent.oaistatic.com/codex-app-prod/Codex.dmg)
*   mac intel 下载地址：[https://persistent.oaistatic.com/codex-app-prod/Codex-latest-x64.dmg](https://persistent.oaistatic.com/codex-app-prod/Codex-latest-x64.dmg)

### 成果展示

![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753114/markdown/test-md/Pasted-image-20260606204013.png)
  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753118/markdown/test-md/Pasted-image-20260606204023.png)

如果你也是小白，可以根据我的操作一步一步来，其实很简单的。  
cpa 和 sub2api 两个软件二选一即可。

### CLIProxyAPI 的使用

#### CLIProxyAPI 安装

从项目中下载好压缩包后解压，复制一份 config.example.yaml 为 config.yaml 文件  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752971/markdown/test-md/Pasted-image-20260605231723.png)

修改 config.json 配置文件，只需要修改登录密码，例如修改为 123456

*   secret-key: "123456"  
    ![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752967/markdown/test-md/Pasted-image-20260605230222.png)
    

使用 cmd 启动 cpa（在路径栏输入 cmd 并回车可以在当前路径下快速启动 cmd），然后在 cmd 中输入 cli-proxy-api.exe 即可以完成启动。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752974/markdown/test-md/Pasted-image-20260605231842.png)
  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752978/markdown/test-md/Pasted-image-20260605235930.png)

#### CLIProxyAPI 如何配置

在浏览器中打开

*   [http://localhost:8317/management.html](http://localhost:8317/management.html)
*   [http://127.0.0.1:8317/management.html](http://127.0.0.1:8317/management.html)  
    密码是刚才配置文件里面修改的 123456  
    ![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752981/markdown/test-md/Pasted-image-20260606000310.png)
    

##### 账号配置

如果你使用的是账号密码登录，则使用\[OAuth 登录\]，如果你使用配置文件登录，则使用\[认证文件\]。

###### OAuth 登录

点击\[OAuth 登录\]->\[开始 Codex 登录\]->\[打开链接\]，后续操作参考页面说明完成即可。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753005/markdown/test-md/Pasted-image-20260606003842.png)

###### 认证文件

点击\[认证文件\]->\[上传文件\]，选择你购买的 cpa.json 文件进行导入即可，后续可在此处看账号情况，例如报错，余额不足，登录过期等情况。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753009/markdown/test-md/Pasted-image-20260606004014.png)
  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753122/markdown/test-md/Snipaste_2026-06-06_00-43-02.png)

##### 密钥配置

配置 API 密钥，用于后续的 API Key

##### 网络配置（可选）

建议配置此选项，如果后续服务出现 503 现象，很大几率是未配置网络造成的网络波动。  
点击\[配置面板\]->\[系统配置\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752998/markdown/test-md/Pasted-image-20260606001155.png)
  
往下滚动找到\[网络配置\]，输入你的网络配置，并且保存。  
常见的例如：socks5://127.0.0.1:7890  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753001/markdown/test-md/Pasted-image-20260606001307.png)

### sub2api 的使用

#### sub2api 的安装

参考项目描述的快速安装方法

 _复制代码_ _隐藏代码_ `mkdir -p /opt/sub2api-deploy && cd /opt/sub2api-deploy


curl -sSL https://raw.githubusercontent.com/Wei-Shaw/sub2api/main/deploy/docker-deploy.sh | bash

cp .env.example .env`

修改 .env 配置文件中的登录账号密码和端口，密码以 123456 为例

 _复制代码_ _隐藏代码_ `ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=123456


SERVER_PORT=8080`

![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753016/markdown/test-md/Pasted-image-20260606010749.png)
  
如果忘记设置密码直接启动，使用以下命令获取日志中的密码

 _复制代码_ _隐藏代码_`docker compose -f docker-compose.local.yml logs sub2api | grep "admin password"`

接下来启动服务

 _复制代码_ _隐藏代码_ `docker compose -f docker-compose.local.yml up -d


docker compose -f docker-compose.local.yml logs -f sub2api`

两个版本的区别  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753012/markdown/test-md/Pasted-image-20260606005805.png)

##### 检查是否成功启动

浏览器打开部署好的服务地址：[http://YOUR\_SERVER\_IP:8080](http://your_server_ip:8080/)  
ip 和端口根据实际情况修改。

#### sub2api 如何配置

在浏览器中打开后台地址，先进行登录，账号密码是在配置文件中设置的。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753125/markdown/test-md/Snipaste_2026-06-06_13-47-35.png)

登录完成后会有教程提示  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753020/markdown/test-md/Pasted-image-20260606134828.png)
  
接下来简单进行几部设置即可开始使用。

##### 分组管理

点击\[分组管理\]->\[添加分组\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753024/markdown/test-md/Pasted-image-20260606135035.png)
  
输入\[名称\]和选择\[平台\]（这里我用的是ChatGPT，选择OpenAI）  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753027/markdown/test-md/Pasted-image-20260606135149.png)
  
往下滑动找到\[图片生成计费\]，勾选\[允许当前分组生图\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753128/markdown/test-md/Snipaste_2026-06-06_13-59-16.png)
  
最后点击\[创建\]即可完成分组设置。

##### 账号管理

###### 账号登录

此方法是手动进行账号登录。  
点击\[账号管理\]->\[添加账号\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753031/markdown/test-md/Pasted-image-20260606140509.png)
  
输入\[账号名称\]，平台选择\[OpenAI\]，账号类型选择\[OAuth\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753034/markdown/test-md/Pasted-image-20260606140624.png)
  
滑动到最底部，勾选刚才创建的分组，然后点击下一步  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753038/markdown/test-md/Pasted-image-20260606140719.png)
  
接下来按照页面提示完成授权即可  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753041/markdown/test-md/Pasted-image-20260606140806.png)

###### 账号导入

此方法适用于导入 sub2api.json 文件。  
点击\[账号管理\]->\[更多操作\]->\[导入\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753045/markdown/test-md/Pasted-image-20260606140914.png)
  
上传 sub2api.json 文件，并点击开始导入。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753048/markdown/test-md/Pasted-image-20260606140949.png)
  
导入后会显示账号状态，例如第一条是正常数据，第二条则是账号登录过期。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753051/markdown/test-md/Pasted-image-20260606141152.png)
  
如果不确定状态，则可以通过\[更多\]->\[测试连接\]，按照页面提示进行测试。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753054/markdown/test-md/Pasted-image-20260606141253.png)

导入完成后需要进行设置，点击\[编辑\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753057/markdown/test-md/Pasted-image-20260606141530.png)
  
往下找到 Codex 图片生成桥接，选择强制开启  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753060/markdown/test-md/Pasted-image-20260606141651.png)
  
往下找到分组，勾选刚才创建的分组，并点击更新，即可完成账号的设置。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753063/markdown/test-md/Pasted-image-20260606141740.png)

##### 创建 API 密钥

创建 API 密钥，用于后续连接使用。  
默认的 API 请求地址是：[http://YOUR\_SERVER\_IP:8080](http://your_server_ip:8080/)  
点击 \[API 密钥\]->\[创建密钥\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753067/markdown/test-md/Pasted-image-20260606193129.png)
  
输入\[名称\]，并选择好刚才创建的\[分组\]，点击\[创建\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753071/markdown/test-md/Pasted-image-20260606193703.png)
  
后续使用可以点击此处复制密钥  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753074/markdown/test-md/Pasted-image-20260606193846.png)

##### 添加余额

点击\[用户管理\]->\[充值\]  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753077/markdown/test-md/Pasted-image-20260606193934.png)
  
给自己增加一些余额并确认，至此完成了 sub2api 的设置  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753081/markdown/test-md/Pasted-image-20260606194006.png)

### cc-switch 的使用

从项目地址下载并安装好后，打开 cc-switch。  
先切换到\[codex\]，然后点击创建  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753084/markdown/test-md/Pasted-image-20260606194917.png)

如果是使用 DeepSeek 的模型，选择这个进行导入  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753088/markdown/test-md/Pasted-image-20260606195011.png)

如果是自己搭建了 cpa 或者 sub2api 则使用自定义配置，往下找到以下信息并填写。

#### cpa 填写内容

*   供应商名称：输入自定义的名称
*   API Key：在 cpa 的\[配置面板\]->\[认证配置\]中生成的密钥
*   API 请求地址：[http://127.0.0.1:8317/v1/](http://127.0.0.1:8317/v1/)  
    ![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753091/markdown/test-md/Pasted-image-20260606195224.png)
    

填写完成后直接点击添加即可

#### sub2api 填写内容

可以直接在后台中导入  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753095/markdown/test-md/Pasted-image-20260606195614.png)
  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753131/markdown/test-md/Snipaste_2026-06-06_20-05-51.png)

也可以手动填写

*   供应商名称：输入自定义的名称
*   API Key：在 cpa 的\[配置面板\]->\[认证配置\]中生成的密钥
*   API 请求地址：[http://127.0.0.1:8080](http://127.0.0.1:8080/)  
    ![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753098/markdown/test-md/Pasted-image-20260606195709.png)
    

#### 配置使用

需要点击启用以应用配置  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753100/markdown/test-md/Pasted-image-20260606195812.png)
  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753104/markdown/test-md/Pasted-image-20260606195820.png)

### codex 的使用

从项目地址下载安装好 codex++ 后，打开 codex++ 管理工具  
点击\[供应商配置\]->\[联动 cc-switch\]，此时会自动加载 cc-switch 的配置，然后点击\[重启Codex++\]来启动 codex，注意需要使用 codex++ 管理工具来启动 codex，防止无法正常加载插件。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753107/markdown/test-md/Pasted-image-20260606200036.png)

使用 codex++ 启动 codex，第一次进入会让选择，可以直接跳过。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752947/markdown/test-md/Pasted-image-20260605225245.png)

点击继续后，即可看见正常的窗口界面  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752950/markdown/test-md/Pasted-image-20260605225438.png)

可以简单发一句 hi 进行测试，是否连接正常  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752955/markdown/test-md/Pasted-image-20260605225525.png)

#### 关于 codex 的语言

一开始进入默认是英语，语言包需要网络进行加载，等加载完成会自动切换成中文，也可以自己进入设置进行修改。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780753111/markdown/test-md/Pasted-image-20260606200526.png)

#### 关于插件

登录进来后，插件应该是解锁了，里面可以看见热门的 Computer use 和 Chrome 插件，用于 codex 操作电脑和 chrome 浏览器，就是有点费 token。

为什么只有这3个插件呢？请点击这个地方  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752958/markdown/test-md/Pasted-image-20260605225712.png)
  
如果你的插件安装加载正确，这个位置会有插件市场可以切换，此时就能看见其他的插件了。  
![](https://res.cloudinary.com/dmavyp7hh/image/upload/v1780752964/markdown/test-md/Pasted-image-20260605225805.png)

#### 关于技能

ai 在正常情况下是不会回复你的逆向相关问题，但是可以使用 ctf-skills，里面包含了 ctf 常见的技能。  
项目地址：[https://github.com/ljagiello/ctf-skills](https://github.com/ljagiello/ctf-skills)