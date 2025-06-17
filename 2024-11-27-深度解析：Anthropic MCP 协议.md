# 深度解析：Anthropic MCP 协议
> 正如 LSP 成为了 IDE 的通用标准一样，Anthropic 正在将 MCP 打造成 LLM 集成的开放标准。

前段时间 OpenAI 发布了一个实时访问第三方应用的功能来为 ChatGPT 提供上下文（[ChatGPT 升级为实时协作助手](https://mp.weixin.qq.com/s?__biz=MzIzNjE2NTI3NQ==&mid=2247489466&idx=1&sn=1e2180cd094393b134b45c99b46dcc1c&scene=21#wechat_redirect)），没想到 Claude 这么快就带来了一个 LLM 协议标准，直接将 AI 能力拉满（现在下结论为时尚早）。不过当我看完整个协议以及简单上手体验后，我想说：“真牛逼，它以一种非入侵方式最大限度获取到系统权限来拓展 AI 的能力边界”！

模型上下文协议（MCP）是 Anthropic 推出的开放标准，旨在通过统一的`客户端-服务器`架构解决 LLM 应用与数据源连接的难题。它支持通过同一协议访问本地资源（如数据库、文件）和远程资源（如 Slack、GitHub API），无需定制集成。MCP 不仅共享数据，还可公开工具和交互模板，且内置安全性，确保资源由服务器完全掌控。目前 MCP 支持本地运行，未来将引入企业级认证的远程支持，实现团队间的安全共享。通过 Claude 桌面应用，开发者可在短时间内集成 MCP，快速连接多种数据源，推动 AI 集成的标准化发展。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSN6sibcbmmprSMLzmwsTQBRSBPYJnUPGpdMIHhlibRLvA9sM0FInSib1xg/640?wx_fmt=png&from=appmsg)

近日，Model Context Protocol\[1\]（MCP，模型上下文协议）正式开源。作为一项连接 AI 助手与数据系统的新标准，MCP 的诞生旨在解决当前 AI 模型因数据孤岛限制而无法充分发挥潜力的难题。这项由 Claude 推动的技术创新为开发者提供了一个开放的、统一的解决方案，使 AI 系统能够与多种内容存储库、业务工具和开发环境高效对接，显著提升模型的响应质量与相关性。

背景
--

> 解决碎片化问题，为 AI 打开数据大门。

当前，AI 助手已成为主流工具，模型能力的进步使推理和质量得以迅速提升。然而，数据访问的瓶颈依然存在。每个数据源需要独立的定制集成，这种碎片化的方式不仅效率低下，还限制了 AI 的可扩展性。

MCP 的出现就是为了改变现状。它作为一个通用的开放协议，为数据源与 AI 系统之间的连接提供了统一标准，替代复杂的多源整合方式。这种设计极大简化了数据接入过程，降低开发者的工作量，同时让 AI 系统能够更加全面和准确地访问数据，推动系统从孤立走向协同。

MCP 核心
------

MCP 的架构清晰且开放，开发者可以通过 MCP 服务器对外提供数据，或构建 MCP 客户端，将 AI 应用与这些服务器连接。为推动开发者快速上手，MCP 开源了以下三大核心工具：

*   **MCP 规范及 SDK**：帮助开发者轻松理解和实现协议功能。
    

*   MCP 官网：`https://modelcontextprotocol.io`
    
*   MCP GitHub：`https://github.com/modelcontextprotocol`
    

*   **本机 MCP 服务支持**：通过 Claude 桌面应用快速实现本地化数据连接，应用安装链接 `https://claude.ai/download`。
    
*   **开源服务代码库**：包含 Google Drive、Slack、GitHub 等流行系统的预构建实现，便于直接部署和测试。访问链接 `https://github.com/modelcontextprotocol/servers`。
    

此外，Claude 3.5 Sonnet 模型还支持快速开发 MCP 服务器，使个人和企业能够以最低的门槛实现与重要数据集的对接。

行业动态
----

目前，MCP 已被 Block 和 Apollo 等企业率先应用，并逐步融入 Zed\[2\]（Zed MCP 源码实现 context\_server/protocol.rs\[3\]）、Replit\[4\]、Codeium\[5\] 和 Sourcegraph\[6\] 等开发工具平台。这些公司通过 MCP 增强 AI 对上下文的理解能力，使 AI 能够在编码任务中高效检索相关信息，生成更准确、更具功能性的代码。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSpKvJX153ekoXWAcclPYSSS1iaWG7VWLV1VlRuvjcpaGb3J9xfeEDYxQ/640?wx_fmt=png&from=appmsg)

Block 的首席技术官 Dhanji R. Prasanna 表示：“在 Block，开源不仅仅是一种开发模式，它是我们工作的基石，更是一种承诺——致力于创造能够推动深远变革、造福公众的技术。像 Model Context Protocol 这样的开源技术，是将 AI 与现实应用连接起来的桥梁，确保创新以开放、透明和协作为核心。我们非常高兴能参与这一协议的开发，并借助它构建自主化系统，让人们摆脱机械性任务的束缚，专注于更具创造性的工作。”

通过 MCP，开发者不再需要为每个数据源维护独立的连接器，而是可以基于标准协议构建一套通用的解决方案。随着生态系统的不断完善，AI 系统将能够在不同工具和数据集之间保持上下文一致性，为企业和开发者带来更具前景的技术架构。

未来展望
----

Claude 团队表示，他们致力于将 MCP 打造成一个协作性的开源生态系统，鼓励开发者、企业以及早期技术探索者共同参与，推动具有上下文感知能力的 AI 工具走向更广阔的未来。

开发者目前可以通过 Claude 桌面应用快速部署 MCP 服务，也可以根据官方提供的快速入门指南构建自己的 MCP 解决方案。同时，开源社区已开放了连接器和实现的代码库，支持开发者贡献自己的扩展功能。

随着 MCP 的普及，AI 系统将更好地突破数据隔离的限制，真正实现与现实环境的无缝对接。对于技术领域而言，这无疑是一次重要的里程碑，也为 AI 生态的可持续发展带来了全新可能。

我自己根据文档几分钟就跑通了本地数据库连接，在开始前需要做一些额外准备：

*   打开桌面应用的开发者模式，方便进行日志调试（菜单 `Help → Enable Developer Mode -> 点击弹窗 Enable 按钮`）。
    
    ![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSZAvMXzY9AW4m1IAdqUxnMWgpA4qter8LsbMDe9QVk1P32sq6UQA0ww/640?wx_fmt=png&from=appmsg)
    
*   启用开发者模式后，会在菜单中多一个 `Developer` 菜单项，点击 `Open MCP Log File` 可以打开日志文件，查看到操作日志，方便排查问题。
    
    ![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSYvvkevcV1ay9Ij4eia2rX3TvNUfeWfM5YGK0QPCWPCAGVXGynRCUfzg/640?wx_fmt=png&from=appmsg)
    

> 📌 前置条件
> 
> *   macOS 或 Windows 系统
>     
> *   已安装最新版本的 Claude 桌面应用（当前为 0.7.1 版本）
>     
> *   uv\[7\] 0.4.18 或更高版本（可通过 `uv --version` 检查）
>     
> *   Git（`git --version` 检查）
>     
> *   SQLite（`sqlite3 --version` 检查）
>     
> 
> 如果系统环境不存在 uv、Git、SQLite，可通过以下方式在命令行中进行安装：
> 
> **macOS 安装**
> 
> ```
> # Using Homebrewbrew install uv git sqlite3# Or download directly:# uv: https://docs.astral.sh/uv/# Git: https://git-scm.com# SQLite: https://www.sqlite.org/download.html
> ```
> 
> **Windows 安装**
> 
> ```
> # Using wingetwinget install --id=astral-sh.uv -ewinget install git.git sqlite.sqlite# Or download directly:# uv: https://docs.astral.sh/uv/# Git: https://git-scm.com# SQLite: https://www.sqlite.org/download.html
> ```

操作步骤
----

*   设置本地 SQLite 数据库
    
*   通过 MCP 将 Claude 桌面应用连接到该数据库
    
*   安全地查询和分析数据
    

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSOqYYgTay5uVrMblfG04yCKBKUGCAsexgn2cl5ADVYiaPAS7yBBVbsGQ/640?wx_fmt=png&from=appmsg)

### Step 1：创建测试数据库

macOS 请执行以下命令（路径：`/Users/YOUR_USERNAME/test.db`）：

```
sqlite3 ~/test.db <<EOFCREATE TABLE products (  id INTEGER PRIMARY KEY,  name TEXT,  price REAL);INSERT INTO products (name, price) VALUES  ('Widget', 19.99),  ('Gadget', 29.99),  ('Gizmo', 39.99),  ('Smart Watch', 199.99),  ('Wireless Earbuds', 89.99),  ('Portable Charger', 24.99),  ('Bluetooth Speaker', 79.99),  ('Phone Stand', 15.99),  ('Laptop Sleeve', 34.99),  ('Mini Drone', 299.99),  ('LED Desk Lamp', 45.99),  ('Keyboard', 129.99),  ('Mouse Pad', 12.99),  ('USB Hub', 49.99),  ('Webcam', 69.99),  ('Screen Protector', 9.99),  ('Travel Adapter', 27.99),  ('Gaming Headset', 159.99),  ('Fitness Tracker', 119.99),  ('Portable SSD', 179.99);EOF
```

Windows 用户执行以下命令（路径：`C:\\Users\\YOUR_USERNAME\\test.db`）：

```
$sql = @'CREATE TABLE products (  id INTEGER PRIMARY KEY,  name TEXT,  price REAL);INSERT INTO products (name, price) VALUES  ('Widget', 19.99),  ('Gadget', 29.99),  ('Gizmo', 39.99),  ('Smart Watch', 199.99),  ('Wireless Earbuds', 89.99),  ('Portable Charger', 24.99),  ('Bluetooth Speaker', 79.99),  ('Phone Stand', 15.99),  ('Laptop Sleeve', 34.99),  ('Mini Drone', 299.99),  ('LED Desk Lamp', 45.99),  ('Keyboard', 129.99),  ('Mouse Pad', 12.99),  ('USB Hub', 49.99),  ('Webcam', 69.99),  ('Screen Protector', 9.99),  ('Travel Adapter', 27.99),  ('Gaming Headset', 159.99),  ('Fitness Tracker', 119.99),  ('Portable SSD', 179.99);'@cd ~& sqlite3 test.db $sql
```

### Step 2：配置 Claude 应用

配置文件路径：

*   macOS：`~/Library/Application Support/Claude/claude_desktop_config.json`
    
*   Windows：`%APPDATA%\Claude\claude_desktop_config.json`
    

文件可通过命令打开，也可以通过 Claude 设置界面打开（点击 `编辑配置（Edit Config）` 按钮）。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSvHIicquJ9NdnKVsov9KOdvJjctvPGI5k8nKNuicfHLkdvTBamG2SNd3g/640?wx_fmt=png&from=appmsg)

用自己喜欢的编辑器将以下内容复制到 `claude_desktop_config.json` 中。注意将 `/Users/lencx/test.db` 路径改为自己的本机文件路径。

```
{  "mcpServers": {    "sqlite": {      "command": "uvx",      "args": [        "mcp-server-sqlite",        "--db-path",        "/Users/lencx/test.db"      ]    }  }}
```

这里告诉 Claude 桌面应用：

*   有一个名为 “sqlite” 的 MCP 服务器
    
*   通过运行 `uvx mcp-server-sqlite` 命令来启动它
    
*   将其连接到你的测试数据库（即本地创建的 test.db 文件）
    
*   保存文件后，重新启动 Claude 桌面应用
    

### Step 3：测试一下

将以下 Prompt 发送给 Claude，来验证一切是否正常：

`Can you connect to my SQLite database and tell me what products are available, and their prices?`

如果一切正常，Claude 将连接到 SQLite MCP 服务器，然后查询本地数据库，使用格式化方式呈现出结果。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtS4riaPkbYtRYEnF3EvbRR7C3Oic5ToybCoMybPXyggL9GW2PtibtIB2Nag/640?wx_fmt=png&from=appmsg)

你还可以测试这些 Prompt：

*   基本查询：`What's the average price of all products in the database?`
    
*   数据分析：`Can you analyze the price distribution and suggest any pricing optimizations?`
    
*   复杂操作：`Could you help me design and create a new table for storing customer orders?`
    

运行原理
----

当你通过 MCP 与 Claude 桌面应用交互时，会经过以下步骤：

1.  **服务器发现**：Claude 桌面应用在启动时会连接到你配置的 MCP 服务器。
    
2.  **协议握手**：当你询问数据时，Claude 桌面应用会：
    

*   确定哪个 MCP 服务器可以提供帮助（例如，本例中的 SQLite 服务器）。
    
*   通过协议协商服务器的功能和权限。
    
*   向 MCP 服务器请求数据或执行操作。
    

4.  **交互流程**：
    

*   Claude 桌面应用通过 MCP 服务器与本地资源交互。
    
*   所有操作均严格限制在服务器允许的范围内。
    

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSXxpppWbx7Z9MUrGsxqkViadkU3yXibN5yfDuuhLvkn9nDmP4cb7GjbDw/640?wx_fmt=png&from=appmsg)

在安全性方面：

*   **受控能力**：MCP 服务器仅暴露特定且受控的功能。
    
*   **本地运行**：MCP 服务器运行在本地计算机上，访问的资源不会暴露在互联网中。
    
*   **用户确认**：对于敏感操作，Claude 桌面应用需要用户确认后才能执行。
    

这一设计确保了在使用 Claude 分析或交互本地数据时，用户始终保持对数据访问和操作的完全控制权，同时最大限度保障数据安全性。

常见问题
----

如果 Claude 桌面应用中没有显示内容，可以通过以下步骤排查问题：首先，检查是否启用了 MCP，点击聊天框旁的 **🔌 图标**，展开“已安装的 MCP 服务器”（Installed MCP Servers）确认配置的服务器是否显示。然后导航到 **Claude > Settings…** 打开“开发者（Developer）”标签页验证配置。最后完全退出并重启 Claude 桌面应用以确保更改生效。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSIQVSO6kefUgwwamq5pBOvZsKCsqDvuqiaJicGPETkzE1qR0suVrhW4TA/640?wx_fmt=png&from=appmsg)

如果遇到 MCP 或数据库错误，可以检查 Claude 桌面应用的日志，运行命令 `tail -n 20 -f ~/Library/Logs/Claude/mcp*.log` 查看最近的日志信息。也可以测试数据库连接，例如运行 `sqlite3 ~/test.db ".tables"` 确认数据库是否正常工作。常见的修复方法包括检查配置文件中的文件路径、验证数据库文件的权限，以及确保 SQLite 已正确安装。通过这些步骤，可以有效解决大部分问题。

> 官方文档内容很长，为了方便大家对 MCP 有一个全面了解，我对文档做了简单梳理。**需要注意：目前文档主要适配 macOS，其他系统指南将在晚些时候给出。** 

快速开始
----

目前 MCP 有三种方式可以帮助你快速开始，Python 或 TypeScript 选一个自己比较熟悉的构建服务即可。

*   快速入门（MCP Quickstart\[8\]）：不到 5 分钟即可开始使用 MCP，可在 Claude 桌面应用和本地服务之间建立安全连接（**以上的 “lencx 演示” 就是基于该部分文档实现**）。
    
*   构建第一个 Python 服务 (MCP Python\[9\])：15 分钟内用 Python 创建一个简单的 MCP 服务器。
    
*   构建第一个 TypeScript 服务（MCP TypeScript\[10\]）：15 分钟内用 TypeScript 创建一个简单的 MCP 服务器。
    

开发工具
----

开发 MCP 服务器或将其与应用程序集成时，有效的调试至关重要。所以 MCP 提供了几种不同层次的调试工具：

*   **MCP 检查器（MCP Inspector\[11\]）**
    

*   交互式调试界面
    
*   直接服务器测试
    

*   **Claude 桌面开发工具（Claude Desktop Developer Tools）**
    

*   集成测试
    
*   日志收集
    
*   Chrome DevTools 集成
    

*   **服务器日志（Server Logging）**
    

*   自定义日志记录实现
    
*   错误追踪
    
*   性能监控
    

概念：核心架构（Core architecture）
--------------------------

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSTSyPh27NquzXcoMxiaXjefpkYSfYsuBsH6g4Oj4ujJA3gJhsmav6h0A/640?wx_fmt=png&from=appmsg)

MCP 遵循客户端-服务器架构（client-server），其中：

*   **MCP 主机（MCP Hosts）**：希望通过 MCP 访问资源的程序（例如 Claude Desktop、IDE 或 AI 工具），用于发起连接。
    
*   **MCP 客户端（MCP Clients）**：与服务器保持 1:1 连接的协议客户端。
    
*   **MCP 服务器（MCP Servers）**：轻量级程序，每个程序都通过标准化模型上下文协议公开特定功能。为客户端提供上下文、工具和 prompt 信息。
    
*   **本地资源（Local Resources）**：你的计算机资源中可供 MCP 服务器安全访问的资源（数据库、文件、服务）。
    
*   **远程资源（Remote Resources）**：MCP 服务器可以连接到的互联网资源（例如通过 API）。
    

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSUkkVo4S2x5S0tAcbFSWjJIhrlypHmLg8DvRia9r30oaQLgHXGVb0xtg/640?wx_fmt=png&from=appmsg)

### 核心组件

**`协议层（Protocol layer）`**

协议层负责消息的封装、请求/响应的关联，以及高层通信模式的管理。 主要类包括： **Protocol**  、**Client** 、 **Server** 等。以 Protocol 类为例（TypeScript 版）：

```
class Protocol<Request, Notification, Result> {    // Handle incoming requests    setRequestHandler<T>(schema: T, handler: (request: T, extra: RequestHandlerExtra) => Promise<Result>): void    // Handle incoming notifications    setNotificationHandler<T>(schema: T, handler: (notification: T) => Promise<void>): void    // Send requests and await responses    request<T>(request: Request, schema: T, options?: RequestOptions): Promise<T>    // Send one-way notifications    notification(notification: Notification): Promise<void>}
```

**`传输层（Transport layer）`**

传输层负责客户端和服务器之间的实际通信。MCP 支持多种传输机制：

*   **Stdio 传输**
    

*   使用标准输入/输出进行通信
    
*   适合本地进程间通信
    

*   **基于 HTTP 和 SSE 的传输**
    

*   使用 **Server-Sent Events（SSE）** 进行服务器到客户端的消息传递
    
*   使用 **HTTP POST** 进行客户端到服务器的消息传递
    

所有传输机制都采用 **JSON-RPC 2.0** 协议进行消息交换。详细的 MCP 消息格式规范可参考相关文档。

**`消息类型（Message types）`**

MCP 定义了以下主要消息类型：

*   **请求（Request）**：需要另一方提供响应
    
    ```
    interface Request {  method: string;  params?: { ... };}
    ```
    
*   **通知（Notification）**：单向消息，不需要响应
    
    ```
    interface Notification {  method: string;  params?: { ... };}
    ```
    
*   **结果（Result）**：成功响应请求的消息
    
    ```
    interface Result {  [key: string]: unknown;}
    ```
    
*   **错误（Error）**：表示请求失败的消息
    
    ```
    interface Error {  code: number;  message: string;  data?: unknown;}
    ```
    

### Connection 生命周期

**`初始化（Initialization）`**

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSuCW6qCqVkKicFHdeiaickniasCJCrcdVwA1g3oVoUdd0sNLZDyMP21dI3Q/640?wx_fmt=png&from=appmsg)

*   客户端发送 `initialize` 请求，包含协议版本和能力信息
    
*   服务器响应其协议版本和能力信息
    
*   客户端发送 `initialized` 通知以确认
    
*   正常消息交换开始
    

**`消息交换（Message exchange）`**

初始化后，支持以下通信模式：

*   **请求-响应模式（Request-Response）**：客户端或服务器发送请求，另一方响应
    
*   **通知模式（Notifications）**：任一方发送单向消息
    

**`终止连接（Termination）`**

任一方可以终止连接：

*   通过 `close()` 进行正常关闭
    
*   通过传输层断开连接
    
*   因错误条件导致中断
    

**`错误处理（Error handling）`**

错误通过以下方式传播：

*   请求的错误响应
    
*   传输中的错误事件
    
*   协议级错误处理程序
    

```
enum ErrorCode {  // Standard JSON-RPC error codes  ParseError = -32700,  InvalidRequest = -32600,  MethodNotFound = -32601,  InvalidParams = -32602,  InternalError = -32603}
```

SDK 和应用程序可以自定义 `-32000` 以上的错误码。

**`代码示例`**

以下是实现 MCP 服务器的基本代码示例：

```
import { Server } from "@modelcontextprotocol/sdk/server/index.js";import { StdioServerTransport } from "@modelcontextprotocol/sdk/server/stdio.js";const server = new Server({  name: "example-server",  version: "1.0.0"}, {  capabilities: {    resources: {}  }});// Handle requestsserver.setRequestHandler(ListResourcesRequestSchema, async () => {  return {    resources: [      {        uri: "example://resource",        name: "Example Resource"      }    ]  };});// Connect transportconst transport = new StdioServerTransport();await server.connect(transport);
```

概念：资源（Resources）
----------------

资源是模型上下文协议（MCP）的核心组件之一，允许服务器将数据和内容暴露给客户端，以便用作 LLM 交互的上下文信息。MCP 资源设计为由应用程序控制，这意味着客户端应用程序可以决定资源的使用方式和时机。例如：

*   某些应用可能需要用户显式选择资源。
    
*   另一些应用可能基于启发式算法或 AI 模型自身的判断自动选择资源。
    

所以资源代表 MCP 服务器希望向客户端提供的任何类型的数据，包括：

*   文件内容（File contents）
    
*   数据库记录（Database records）
    
*   API 响应（API responses）
    
*   实时系统数据（Live system data）
    
*   屏幕截图和图像（Screenshots and images）
    
*   日志文件（Log files）
    
*   ...
    

每个资源通过唯一的 URI 标识，可以包含文本或二进制数据。

### 资源 URI

资源通过以下格式的 URI 进行标识（`[协议]://[主机]/[路径]`）：

```
[protocol]://[host]/[path]
```

示例：

*   `file:///home/user/documents/report.pdf`
    
*   `postgres://database/customers/schema`
    
*   `screen://localhost/display1`
    

协议和路径结构由 MCP 服务器实现定义，服务器也可以自定义 URI 方案。

### 资源类型

资源可以包含以下两种内容类型：

*   **文本资源**：文本资源包含 UTF-8 编码的文本数据，适用于：源代码、配置文件、日志文件、JSON/XML 数据、纯文本等。
    
*   **二进制资源**：二进制资源包含以 Base64 编码的原始二进制数据，适用于：图像、PDF 文件、音频文件、视频文件、其他非文本格式等。
    

### 资源发现

客户端主要通过两种方式发现可用资源：

*   **直接资源（Direct resources）**：服务器通过端点公开具体资源的列表 `resources/list`。
    
    ```
    {  uri: string;           // Unique identifier for the resource  name: string;          // Human-readable name  description?: string;  // Optional description  mimeType?: string;     // Optional MIME type}
    ```
    
*   **资源模板（Resource templates）**：对于动态资源，服务器可以公开 URI 模板\[12\]，客户端可以使用它来构建有效的资源 URI。
    
    ```
    {  uriTemplate: string;   // URI template following RFC 6570  name: string;          // Human-readable name for this type  description?: string;  // Optional description  mimeType?: string;     // Optional MIME type for all matching resources}
    ```
    
*   **阅读资源（Reading resources）**：要读取资源，客户端 `resources/read` 需要使用资源 URI 发出请求。服务器以资源内容列表进行响应。
    
    ```
    {  contents: [    {      uri: string;        // The URI of the resource      mimeType?: string;  // Optional MIME type      // One of:      text?: string;      // For text resources      blob?: string;      // For binary resources (base64 encoded)    }  ]}
    ```
    

### 资源更新

MCP 通过两种机制支持资源的实时更新：

*   **列出更改（List changes）**：当可用资源列表发生变化时，服务器可以通过 `notifications/resources/list_changed` 通知客户端
    
*   **内容变更（Content changes）**：用户可以订阅特定资源的更新
    

*   客户端发送 `resources/subscribe` 资源 URI
    
*   `notifications/resources/updated` 资源发生变化时服务器发送
    
*   客户端可以使用 `resources/read`
    
*   客户端可以取消订阅 `resources/unsubscribe`
    

> 📌 最佳实践
> 
> 使用清晰且具有描述性的资源名称和 URI，提供有助于 LLM 理解的资源描述，并为已知资源设置合适的 MIME 类型。动态内容可以通过资源模板实现，而对于频繁变化的资源，建议使用订阅机制。此外，应优雅地处理错误，提供明确的错误信息，对于大规模资源列表可以使用分页，并在适当情况下对资源内容进行缓存。URI 在处理前需要验证，同时记录任何自定义的 URI 方案以便后续参考。
> 
> 在暴露资源时，安全性至关重要。必须验证所有资源 URI，实施适当的访问控制，并清理文件路径以防止目录遍历攻击。对二进制数据的处理需特别谨慎，可以考虑为资源读取操作设置速率限制并对资源访问进行审计。传输中的敏感数据应加密，MIME 类型需要验证，同时为长时间运行的读取操作设置超时机制。最后，资源的清理操作也应妥善处理，确保系统稳定性和安全性。

### 代码实现

以下是在 MCP 服务器中实现资源支持的简单示例：

```
const server = new Server({  name: "example-server",  version: "1.0.0"}, {  capabilities: {    resources: {}  }});// List available resourcesserver.setRequestHandler(ListResourcesRequestSchema, async () => {  return {    resources: [      {        uri: "file:///logs/app.log",        name: "Application Logs",        mimeType: "text/plain"      }    ]  };});// Read resource contentsserver.setRequestHandler(ReadResourceRequestSchema, async (request) => {  const uri = request.params.uri;  if (uri === "file:///logs/app.log") {    const logContents = await readLogFile();    return {      contents: [        {          uri,          mimeType: "text/plain",          text: logContents        }      ]    };  }  throw new Error("Resource not found");});
```

概念：Prompts
----------

Prompts 允许服务器定义可重用的 prompt 模板和工作流，方便客户端呈现给用户和 LLM。这是一种强大的方法，可以标准化并共享常见的 LLM 交互。Prompts 设计为由用户控制，这意味着它们从服务器暴露给客户端，供用户显式选择使用。

MCP 中的 Prompts 是预定义的模板，具备以下功能：

*   接受动态参数
    
*   包含来自资源的上下文
    
*   链接多个交互
    
*   引导特定工作流
    
*   以用户界面（UI）元素形式呈现（如斜杠命令）
    

### Prompt 结构定义

```
{  name: string;              // Unique identifier for the prompt  description?: string;      // Human-readable description  arguments?: [              // Optional list of arguments    {      name: string;          // Argument identifier      description?: string;  // Argument description      required?: boolean;    // Whether argument is required    }  ]}
```

### 发现 Prompts

客户端可以通过 `prompts/list` 端点发现可用的 prompt：

```
// Request（请求）{  method: "prompts/list"}// Response（响应）{  prompts: [    {      name: "analyze-code",      description: "Analyze code for potential improvements",      arguments: [        {          name: "language",          description: "Programming language",          required: true        }      ]    }  ]}
```

### 使用 Prompts

要使用 prompts，客户端需要发出 `prompts/get` 请求：

```
// Request（请求）{  method: "prompts/get",  params: {    name: "analyze-code",    arguments: {      language: "python"    }  }}// Response（响应）{  description: "Analyze Python code for potential improvements",  messages: [    {      role: "user",      content: {        type: "text",        text: "Please analyze the following Python code for potential improvements:\n\n```python\ndef calculate_sum(numbers):\n    total = 0\n    for num in numbers:\n        total = total + num\n    return total\n\nresult = calculate_sum([1, 2, 3, 4, 5])\nprint(result)\n```"      }    }  ]}
```

### 动态 Prompts

Prompts 可以是动态的，主要有两种：

*   嵌入资源上下文（Embedded resource context）
    
    ```
    {  "name": "analyze-project",  "description": "Analyze project logs and code",  "arguments": [    {      "name": "timeframe",      "description": "Time period to analyze logs",      "required": true    },    {      "name": "fileUri",      "description": "URI of code file to review",      "required": true    }  ]}
    ```
    
*   多步骤工作流程（Multi-step workflows）
    
    ```
    const debugWorkflow = {  name: "debug-error",  async getMessages(error: string) {    return [      {        role: "user",        content: {          type: "text",          text: `Here's an error I'm seeing: ${error}`        }      },      {        role: "assistant",        content: {          type: "text",          text: "I'll help analyze this error. What have you tried so far?"        }      },      {        role: "user",        content: {          type: "text",          text: "I've tried restarting the service, but the error persists."        }      }    ];  }};
    ```
    

> 📌 最佳实践
> 
> 在实现 prompts 功能时，应使用清晰且具有描述性的 prompt 名称，为 prompt 及其参数提供详细说明，并验证所有必需参数的完整性。同时，应优雅地处理缺失参数的情况，并考虑为 prompt 模板实现版本控制。在适当情况下，可以缓存动态内容，记录参数的预期格式，并考虑 prompt 的可组合性。此外，需实现错误处理机制，并使用多种输入场景对 prompt 进行充分测试。
> 
> prompt 可通过多种方式集成到客户端用户界面，包括斜杠命令、快捷操作、上下文菜单项、命令面板入口、引导式工作流和交互式表单。对于 prompt 的更新和变更，服务器可以通过 `prompts.listChanged` 能力通知客户端，通过 `notifications/prompts/list_changed` 类型发送通知，客户端则需重新获取 prompt 列表。
> 
> 在安全性方面，需验证所有参数的合法性并清理用户输入以防止恶意内容，同时考虑对 prompt 调用进行速率限制，实施访问控制并审计 prompt 使用情况。对于敏感数据，应适当加密和保护，验证生成内容的安全性，并为 prompt 处理设置超时机制。此外，需注意 prompt 注入攻击的风险，并记录和公开安全需求文档以保障 prompt 的可靠性和安全性。

### 代码示例

以下是在 MCP 服务器中实现 prompts 的完整示例：

```
import { Server } from "@modelcontextprotocol/sdk/server";import {  ListPromptsRequestSchema,  GetPromptRequestSchema} from "@modelcontextprotocol/sdk/types";const PROMPTS = {  "git-commit": {    name: "git-commit",    description: "Generate a Git commit message",    arguments: [      {        name: "changes",        description: "Git diff or description of changes",        required: true      }    ]  },  "explain-code": {    name: "explain-code",    description: "Explain how code works",    arguments: [      {        name: "code",        description: "Code to explain",        required: true      },      {        name: "language",        description: "Programming language",        required: false      }    ]  }};const server = new Server({  name: "example-prompts-server",  version: "1.0.0"}, {  capabilities: {    prompts: {}  }});// List available promptsserver.setRequestHandler(ListPromptsRequestSchema, async () => {  return {    prompts: Object.values(PROMPTS)  };});// Get specific promptserver.setRequestHandler(GetPromptRequestSchema, async (request) => {  const prompt = PROMPTS[request.params.name];  if (!prompt) {    throw new Error(`Prompt not found: ${request.params.name}`);  }  if (request.params.name === "git-commit") {    return {      messages: [        {          role: "user",          content: {            type: "text",            text: `Generate a concise but descriptive commit message for these changes:\n\n${request.params.arguments?.changes}`          }        }      ]    };  }  if (request.params.name === "explain-code") {    const language = request.params.arguments?.language || "Unknown";    return {      messages: [        {          role: "user",          content: {            type: "text",            text: `Explain how this ${language} code works:\n\n${request.params.arguments?.code}`          }        }      ]    };  }  throw new Error("Prompt implementation not found");});
```

概念：工具（Tools）
------------

工具是模型上下文协议（MCP）中的一项强大功能，允许服务器向客户端暴露可执行的功能。通过工具，LLM 可以与外部系统交互、执行计算并在现实世界中采取行动。

工具设计为由模型控制，这意味着工具从服务器暴露给客户端，供 AI 模型自动调用（通常需要人类介入进行授权）。MCP 中的工具允许服务器暴露可被客户端调用的可执行功能，这些功能可供 LLM 用于执行动作。工具的关键特性包括：

*   **发现（Discovery）**：客户端可以通过 `tools/list` 接口列出可用工具。
    
*   **调用（Invocation）**：工具通过 `tools/call` 接口被调用，服务器执行请求的操作并返回结果。
    
*   **灵活性（Flexibility）**：工具的功能范围可以从简单的计算扩展到复杂的 API 交互。
    

与资源类似，工具通过唯一的名称标识，并可以包含描述以指导其使用。然而，与资源不同的是，工具代表动态操作，可以修改状态或与外部系统交互。

### 工具结构定义

```
{  name: string;          // Unique identifier for the tool  description?: string;  // Human-readable description  inputSchema: {         // JSON Schema for the tool's parameters    type: "object",    properties: { ... }  // Tool-specific parameters  }}
```

### 工具模式

以下是服务器可以提供的一些工具类型的示例。

**`系统操作（System operations）`**：与本地系统交互的工具

```
{  name: "execute_command",  description: "Run a shell command",  inputSchema: {    type: "object",    properties: {      command: { type: "string" },      args: { type: "array", items: { type: "string" } }    }  }}
```

**`API 集成（API integrations）`**：包装外部 API 的工具

```
{  name: "github_create_issue",  description: "Create a GitHub issue",  inputSchema: {    type: "object",    properties: {      title: { type: "string" },      body: { type: "string" },      labels: { type: "array", items: { type: "string" } }    }  }}
```

**`数据处理（Data processing）`**：转换或分析数据的工具

```
{  name: "analyze_csv",  description: "Analyze a CSV file",  inputSchema: {    type: "object",    properties: {      filepath: { type: "string" },      operations: {        type: "array",        items: {          enum: ["sum", "average", "count"]        }      }    }  }}
```

### 代码示例

以下是在 MCP 服务器中实现基本工具的示例：

```
const server = new Server({  name: "example-server",  version: "1.0.0"}, {  capabilities: {    tools: {}  }});// Define available toolsserver.setRequestHandler(ListToolsRequestSchema, async () => {  return {    tools: [{      name: "calculate_sum",      description: "Add two numbers together",      inputSchema: {        type: "object",        properties: {          a: { type: "number" },          b: { type: "number" }        },        required: ["a", "b"]      }    }]  };});// Handle tool executionserver.setRequestHandler(CallToolRequestSchema, async (request) => {  if (request.params.name === "calculate_sum") {    const { a, b } = request.params.arguments;    return {      toolResult: a + b    };  }  throw new Error("Tool not found");});
```

概念：采样（Sampling）
---------------

采样是 MCP 的一项强大功能，允许服务器通过客户端请求 LLM 完成，从而实现复杂的代理行为，同时保持安全性和隐私性。目前 Claude 桌面客户端尚未支持此功能。

采样流程包括以下步骤：

1.  服务器向客户端发送 `sampling/createMessage` 请求
    
2.  客户端审查请求内容，并可以对其进行修改
    
3.  客户端向 LLM 请求补全内容
    
4.  客户端对生成的补全内容进行审查
    
5.  客户端将结果返回给服务器
    

这种“人类参与”的设计确保用户对 LLM 可访问的数据和生成的内容保持控制权。

### 消息格式定义

采样请求使用标准化的消息格式：

```
{  messages: [    {      role: "user" | "assistant",      content: {        type: "text" | "image",        // For text:        text?: string,        // For images:        data?: string,             // base64 encoded        mimeType?: string      }    }  ],  modelPreferences?: {    hints?: [{      name?: string                // Suggested model name/family    }],    costPriority?: number,         // 0-1, importance of minimizing cost    speedPriority?: number,        // 0-1, importance of low latency    intelligencePriority?: number  // 0-1, importance of capabilities  },  systemPrompt?: string,  includeContext?: "none" | "thisServer" | "allServers",  temperature?: number,  maxTokens: number,  stopSequences?: string[],  metadata?: Record<string, unknown>}
```

### 请求参数

**`消息（Messages）`**

`messages` 数组包含需要发送给 LLM 的对话历史。每条消息包括：

*   **role**：消息角色，值可以是 `"user"`（用户）或 `"assistant"`（助手）
    
*   **content**：消息内容，可以是：
    

*   **文本内容**：包含 `text` 字段
    
*   **图像内容**：包含 `data`（Base64 编码）和 `mimeType` 字段
    

**`模型偏好（Model preferences）`**

`modelPreferences` 对象允许服务器指定模型选择偏好：

*   **`hints`**：模型名称建议的数组，客户端可以使用这些建议选择合适的模型：
    

*   **name**：字符串，可匹配完整或部分模型名称（如 `"claude-3"` 或 `"sonnet"`）
    
*   客户端可能会将提示映射到不同提供商的等效模型
    
*   多个提示按照优先顺序进行评估
    

*   **优先级**（0-1 范围内归一化）：
    

*   `costPriority`：最小化成本的优先级权重
    
*   `speedPriority`：低延迟响应的优先级权重
    
*   `intelligencePriority`：高模型能力的优先级权重
    

客户端根据这些偏好和可用模型最终决定模型选择。

**`系统提示（System prompt）`**

`systemPrompt` 是一个可选字段，允许服务器请求特定的系统提示。客户端可以修改或忽略此字段。

**`上下文包含（Context inclusion）`**

`includeContext` 参数指定 MCP 上下文的包含范围：

*   `none`：不包含额外上下文
    
*   `thisServer`：仅包含来自请求服务器的上下文
    
*   `allServers`：包含所有连接的 MCP 服务器的上下文
    

客户端最终决定实际包含的上下文内容。

**`采样参数（Sampling parameters）`**

可以使用以下参数微调 LLM 的采样行为：

*   `temperature`：控制生成的随机性（范围：`0.0` 到 `1.0`）
    
*   `maxTokens`：生成的最大标记数
    
*   `stopSequences`：停止生成的序列数组
    
*   `metadata`：附加提供商特定参数
    

### 响应格式

客户端返回完成结果结构体定义：

```
{  model: string,  // Name of the model used  stopReason?: "endTurn" | "stopSequence" | "maxTokens" | string,  role: "user" | "assistant",  content: {    type: "text" | "image",    text?: string,    data?: string,    mimeType?: string  }}
```

以下是向客户请求采样的示例：

```
{  "method": "sampling/createMessage",  "params": {    "messages": [      {        "role": "user",        "content": {          "type": "text",          "text": "What files are in the current directory?"        }      }    ],    "systemPrompt": "You are a helpful file system assistant.",    "includeContext": "thisServer",    "maxTokens": 100  }}
```

> 📌 最佳实践
> 
> 在实现采样功能时，应提供清晰且结构良好的提示，恰当地处理文本和图像内容，并设置合理的标记数限制（token limits）。通过 `includeContext` 参数包含相关上下文，并在使用响应前进行验证，同时优雅地处理错误。此外，应考虑对采样请求实施速率限制，记录预期的采样行为，使用多种模型参数进行测试，并监控采样成本。
> 
> 采样功能设计考虑了人类监督。对于提示，客户端应向用户展示拟定的提示内容，用户可以修改或拒绝提示，系统提示则可以被过滤或修改，上下文包含由客户端控制。对于生成结果，客户端应向用户展示结果，用户可以修改或拒绝生成结果，客户端也可以过滤或修改结果，并由用户决定使用的模型。
> 
> 在安全性方面，需要验证消息内容的合法性，清理敏感信息，并实施速率限制和数据传输加密。同时，妥善处理用户数据隐私，审计采样请求，控制成本暴露风险，设置超时机制，并优雅地处理模型错误。
> 
> 采样支持多种代理式工作流模式，例如读取和分析资源、基于上下文决策、生成结构化数据、处理多步骤任务以及提供交互式协助。上下文管理应请求最小必要的上下文，清晰组织其结构，处理大小限制，根据需要更新上下文并清理过期内容。可靠的错误处理需要捕获采样失败、处理超时错误、管理速率限制、验证响应内容、提供备用行为并记录错误日志。
> 
> 需要注意的是，采样功能存在一些限制，例如依赖客户端能力、用户控制行为、上下文大小限制、速率限制和成本控制。此外，模型的可用性和响应时间可能会有所不同，并非所有内容类型都被支持。

概念：传输（Transports）
-----------------

传输是模型上下文协议（MCP）的核心组件之一，为客户端和服务器之间的通信提供基础。传输机制负责处理消息的发送和接收的底层逻辑。

MCP 使用 **JSON-RPC 2.0** 作为传输格式。传输层负责将 MCP 协议消息转换为 JSON-RPC 格式进行传输，并将接收到的 JSON-RPC 消息还原为 MCP 协议消息。

JSON-RPC 使用三种类型的消息：

*   请求消息（Requests）
    
    ```
    {  jsonrpc: "2.0",  id: number | string,  method: string,  params?: object}
    ```
    
*   响应消息（Responses）
    
    ```
    {  jsonrpc: "2.0",  id: number | string,  result?: object,  error?: {    code: number,    message: string,    data?: unknown  }}
    ```
    
*   通知消息（Notifications）
    
    ```
    {  jsonrpc: "2.0",  method: string,  params?: object}
    ```
    

### 内置传输类型

MCP 包括以下两种标准传输实现：

**标准输入/输出（Input/Output，stdio）**

`stdio` 传输通过标准输入和输出流实现通信，特别适合本地集成和命令行工具。 适用场景：

*   构建命令行工具
    
*   实现本地集成
    
*   需要简单的进程间通信
    
*   与 Shell 脚本协作
    

```
const server = new Server({  name: "example-server",  version: "1.0.0"}, {  capabilities: {}});const transport = new StdioServerTransport();await server.connect(transport);
```

**`服务器发送事件（SSE：Server-Sent Events）`**

`SSE` 传输通过 **HTTP POST** 实现客户端到服务器的通信，同时支持服务器到客户端的流式传输。 适用场景：

*   仅需要服务器到客户端的流式传输
    
*   在受限网络环境中工作
    
*   实现简单的更新机制
    

```
const server = new Server({  name: "example-server",  version: "1.0.0"}, {  capabilities: {}});const transport = new SSEServerTransport("/message", response);await server.connect(transport);
```

**`自定义传输（Custom Transports）`**

MCP 支持轻松实现自定义传输，以满足特定需求。任何传输实现只需符合 `Transport` 接口即可。 你可以为以下场景实现自定义传输：

*   自定义网络协议
    
*   专用通信通道
    
*   与现有系统集成
    
*   性能优化
    

```
interface Transport {  // Start processing messages  start(): Promise<void>;  // Send a JSON-RPC message  send(message: JSONRPCMessage): Promise<void>;  // Close the connection  close(): Promise<void>;  // Callbacks  onclose?: () => void;  onerror?: (error: Error) => void;  onmessage?: (message: JSONRPCMessage) => void;}
```

**`错误处理（Error Handling）`**

传输实现需要处理各种错误场景，包括：

*   连接错误（Connection errors）
    
*   消息解析错误（Message parsing errors）
    
*   协议错误（Protocol errors）
    
*   网络超时（Network timeouts）
    
*   资源清理（Resource cleanup）
    

通过设计健壮的错误处理机制，可以确保传输的稳定性和可靠性。 参考示例：

```
class ExampleTransport implements Transport {  async start() {    try {      // Connection logic    } catch (error) {      this.onerror?.(new Error(`Failed to connect: ${error}`));      throw error;    }  }  async send(message: JSONRPCMessage) {    try {      // Sending logic    } catch (error) {      this.onerror?.(new Error(`Failed to send message: ${error}`));      throw error;    }  }}
```

> 📌 最佳实践
> 
> 在实现或使用 MCP 传输机制时，需要正确管理连接生命周期，确保在连接关闭时清理资源，并使用合适的超时时间。同时，应实现适当的错误处理机制，在发送前验证消息内容，并记录传输事件以便调试。在适当情况下，添加重连逻辑，处理消息队列中的回压问题，并持续监控连接的健康状态。此外，还需要实施必要的安全措施以保证传输的可靠性。
> 
> 在安全方面，需要重点关注身份验证与授权，包括实现可靠的身份验证机制、验证客户端凭证、使用安全的令牌处理方法以及执行授权检查。在数据安全层面，应使用 TLS 加密网络传输，保护敏感数据，验证消息完整性，限制消息大小，并清理输入数据以防止恶意内容。在网络安全层面，需实施速率限制、设置合适的超时时间、处理拒绝服务（DoS）攻击场景、监控异常通信模式，并制定合适的防火墙规则。
> 
> 为有效调试传输问题，可启用调试日志记录、监控消息流量、检查连接状态并验证消息格式，同时测试各种错误场景。使用网络分析工具和错误跟踪工具有助于发现问题。此外，可以通过健康检查和资源使用监控，验证系统在边缘情况和高负载条件下的稳定性，从而确保传输机制的健壮性和安全性。

因 LSP 一定程度上影响了 MCP 的设计理念，所以感觉有必要介绍一下 LSP（非编程人士大概率都没听说过）。

概述
--

语言服务器协议（LSP\[13\]：Language Server Protocol）是一种开放的、基于 JSON-RPC 的通信协议，用于在编辑器或集成开发环境（IDE）与语言服务器之间进行交互。它提供了编程语言的核心功能，如自动补全、跳转到定义、查找所有引用、悬停文档提示等。这一协议通过标准化通信方式，使语言服务器和开发工具之间的协作更加高效。

![](https://mmbiz.qpic.cn/mmbiz_png/90Kxd0FAJJfCsKoL5h2oH2ypr7q7aqtSwnb1w56TeF6xoHUgPGDficGhIwqFibd0UO4wuUH3wMA9tSDFWbcbq0oA/640?wx_fmt=png&from=appmsg)

背景 & 目标
-------

为特定编程语言提供功能（如自动补全、跳转到定义、查找引用）需要耗费大量资源，尤其是传统方式需要针对每种开发工具分别开发插件。这导致重复劳动并增加了开发成本。LSP 的目标是通过标准化协议，解决这一复杂性问题。具体来说：

*   **减少重复工作**：语言社区只需开发一个高性能的语言服务器，而工具社区可以构建一个支持 LSP 的通用扩展模块。
    
*   **实现互操作性**：一个语言服务器可以被多个支持 LSP 的工具使用，而工具也可以支持多种语言。
    
*   **降低开发成本**：开发者可以专注于语言或工具本身，而无需为每个工具或语言重复适配工作。
    

语言服务器 & 客户端
-----------

*   **语言服务器（Language Server）**：提供编程语言的语义分析能力，例如代码补全、跳转到定义等。
    
*   **客户端（Client，编辑器或 IDE）**：与语言服务器通信，展示语言功能并为开发者提供界面交互。
    

通过 LSP，客户端和语言服务器之间的交互基于 JSON-RPC 格式的消息。

核心功能
----

*   **自动补全（Auto Complete）**：提供基于上下文的代码建议。
    
*   **跳转到定义（Go to Definition）**：快速跳转到变量、函数或类的定义位置。
    
*   **查找所有引用（Find All References）**：搜索代码中变量或函数的所有使用位置。
    
*   **悬停提示（Hover Documentation）**：在光标悬停时显示相关的文档或注释。
    
*   **代码重构（Code Refactoring）**：支持重命名、提取函数等代码优化操作。
    

协议基础：JSON-RPC
-------------

LSP 的基础是 JSON-RPC 协议，这种协议定义了请求和响应的结构。在一次典型交互中，客户端会发送请求给语言服务器，例如请求代码补全建议，而语言服务器则根据请求返回执行结果或错误信息。这种基于轻量级 JSON 数据格式的通信方式，不仅使协议实现简单高效，还能适配多种开发环境。

*   **无状态**：每个请求都是独立的，不依赖于先前的交互。
    
*   **轻量级**：协议简单，使用 JSON 格式，易于解析和实现。
    
*   **传输灵活**：可以通过 HTTP、WebSocket 或其他传输协议实现。
    
*   **双向通信**：支持服务器向客户端发送通知（没有响应的请求）。
    

### 请求 & 响应

*   **请求格式**：
    

*   `jsonrpc`：协议版本号（目前固定为 `2.0`）。
    
*   `method`：要调用的方法名称。
    
*   `params`：调用方法所需的参数（可以是数组或对象）。
    
*   `id`：唯一标识请求的 ID，用于匹配响应。
    

*   **响应格式**：
    

*   `jsonrpc`：协议版本号。
    
*   `result`：请求成功时返回的结果。
    
*   `error`：请求失败时返回的错误对象，包含错误码和错误信息。
    
*   `id`：对应请求的 ID，用于区分多个响应。
    

### 代码示例

以下是一个使用 JSON-RPC 进行交互的完整示例：

*   **客户端发送请求**
    
    ```
    {  "jsonrpc": "2.0",  "method": "add",  "params": [5, 3],  "id": 1}
    ```
    
*   **服务器成功响应**
    
    ```
    {  "jsonrpc": "2.0",  "result": 8,  "id": 1}
    ```
    
*   **服务器错误响应**：如果请求的方法不存在或参数错误，返回以下结构
    
    ```
    {  "jsonrpc": "2.0",  "error": {    "code": -32601,    "message": "Method not found"  },  "id": 1}
    ```
    

LSIF
----

LSIF（语言服务器索引格式）是 LSP 的补充协议（发音类似 “else if”），用于以图结构存储编程工件信息。它的目标是支持在开发工具或 Web 界面中进行离线代码导航，无需本地源代码（了解更多区别 LSP vs LSIF\[14\]）。

LSP 的优势
-------

*   **统一的语言支持**：一个语言服务器可以被多种编辑器复用。
    
*   **高效的开发协作**：语言社区专注于语言服务器开发，工具社区专注于客户端扩展开发。
    
*   **扩展性强**：易于支持新语言和新工具，降低成本。
    

例如 CSS LSP 服务器支持 Atom 和 Eclipse 中的 CSS 自动补全。Python、Java 等语言都实现了各自的语言服务器，且已被广泛应用于主流开发工具中。

当前规范与实现
-------

*   最新 LSP 规范为 **3.17** 版本。
    
*   LSIF 的规范正在逐步完善。
    
*   已有许多编程语言（如 Python、Java、JavaScript 等）实现了 LSP，并被集成到多个编辑器（如 VSCode、Sublime Text、Eclipse 等）。
    

微软在核心 LSP 仓库中维护了一份语言服务器实现列表，同时社区站点（如 langserver.org\[15\]）提供了关于各语言服务器和客户端功能的更多信息。

总结
--

语言服务器协议（LSP）通过标准化语言服务器与开发工具的通信方式，极大地提升了开发效率和工具生态的扩展性。它是语言社区和工具社区之间的桥梁，使开发者能够以更低成本享受高级编程功能。LSP 的出现标志着现代开发工具在互操作性和用户体验上的一次重要飞跃。而 MCP 的出现，就是要做 LLM 界的 LSP 标准（野心挺大的）。

### References

\[1\]

**Model Context Protocol:** _https://www.anthropic.com/news/model-context-protocol_

\[2\]

**Zed:** _https://zed.dev/blog/mcp_

\[3\]

**context\_server/protocol.rs:** _https://github.com/zed-industries/zed/blob/3901d4610115989d1b7e4d5c637a297da8219809/crates/context\_server/src/protocol.rs_

\[4\]

**Replit:** _https://replit.com/ai_

\[5\]

**Codeium:** _https://codeium.com_

\[6\]

**Sourcegraph:** _https://sourcegraph.com/blog/cody-supports-anthropic-model-context-protocol_

\[7\]

**uv:** _https://docs.astral.sh/uv/_

\[8\]

**MCP Quickstart:** _https://modelcontextprotocol.io/quickstart_

\[9\]

**MCP Python:** _https://modelcontextprotocol.io/docs/first-server/python_

\[10\]

**MCP TypeScript:** _https://modelcontextprotocol.io/docs/first-server/typescript_

\[11\]

**MCP Inspector:** _https://modelcontextprotocol.io/docs/tools/inspector_

\[12\]

**URI 模板:** _https://datatracker.ietf.org/doc/html/rfc6570_

\[13\]

**LSP:** _https://microsoft.github.io/language-server-protocol_

\[14\]

**LSP vs LSIF:** _https://microsoft.github.io/language-server-protocol/overviews/lsif/overview_

\[15\]

**langserver.org:** _https://langserver.org_
