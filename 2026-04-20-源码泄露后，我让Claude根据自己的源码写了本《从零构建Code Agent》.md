# 2026-04-20-源码泄露后，我让Claude根据自己的源码写了本《从零构建Code Agent》
> Claude Code的源码意外泄露后，有人做了件更有意思的事：让Claude自己分析自己的源码，写出一套完整的Code Agent构建教程。8个章节、从架构到实战，把一个价值数十亿美元的产品拆解成了人人可学的开源课程。

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/XW0OS1TIfjKn3NfPG8bgES5LwHsFUibhIHw1BAcD4QswRqe5mGDrTiaQspQ6yKGRvrQKFKyhaKUT81IVT78YwpxrRfp9HGyVF7hV5HTVicehII/640?from=appmsg&watermark=1#imgIndex=0)

从源码泄露到开源教程

一次泄露，催生了一个开源教程项目
----------------

今天，Anthropic因为打包配置疏忽，把Claude Code的完整源码通过npm的sourcemap文件泄露了出去——1900个文件、51.2万行TypeScript代码，包括大量未发布功能的实现细节。（详见：[Claude Code源码全裸奔：一个57MB的sourcemap文件，扒光了Anthropic最核心的秘密](https://mp.weixin.qq.com/s?__biz=MjM5Njc2NDA5Mg==&mid=2456593682&idx=1&sn=bf8b3877e3b4a281193e5d487514a9cb&scene=21#wechat_redirect)）

泄露事件发生后，开发者社区的反应大致分两派：一派忙着存档代码、分析八卦；另一派则在思考一个更有建设性的问题——**能不能从这些源码中学到什么？**

然后我就想，能不能：**让Claude自己阅读自己的源码，然后写出一套从零构建Code Agent的完整教程**。

这个项目就是 **build-code-agent**（github.com/jiji262/build-code-agent），基于Claude Code v2.1.88的源码分析，用8个章节系统性地拆解了一个工业级Code Agent的方方面面。

![](https://mmbiz.qpic.cn/mmbiz_jpg/XW0OS1TIfjJLKChibF6GgMgdTiceg18zib81d7B0MztSAMm7ibs5GibNRLXraptZcpicjPpAknhcfRGeWe6ibrdQZfmOWDluibh1Gny6HQ5dymG9dQg/640?from=appmsg&watermark=1#imgIndex=1)

项目结构总览

为什么这个项目值得关注？
------------

市面上不缺"教你用Claude API"的入门教程，但**从工业级产品的真实源码出发，逆向拆解其架构设计**——这种学习材料极为稀缺。

Claude Code不是一个玩具项目。它是Anthropic的旗舰开发者工具，每天被数十万开发者用来写代码、审查代码、管理项目。截至2026年初，Claude Code贡献了全球GitHub提交量的4%。

> 这意味着你在学习的不是某个人的Demo，而是一个经过大规模生产验证的Agent架构。

而且教程的作者选择了一个聪明的角度：不是简单地注释源码，而是**从"如何构建"的视角重新组织知识**。每个章节都在回答一个具体问题——如果让你从零开始造一个Claude Code，你需要解决哪些问题？怎么解决？

8个章节拆解一个工业级Agent
----------------

整个教程的章节设计非常有条理，从宏观到微观，从理论到实战：

**第一章：架构总览**

开篇就澄清了一个关键认知：Claude Code不是一个聊天机器人，而是**一个能读文件、写代码、执行命令、管理项目的智能代理操作系统**。

核心架构可以概括为一句话：一个Agent Loop + 工具系统 + 按需加载的技能 + 上下文压缩 + 子代理派生 + 任务依赖图 + 团队协作异步邮箱 + 工作树隔离并行执行 + 权限治理。

> 听起来复杂？其实本质上就是一个while循环不停处理tool\_use调用——"One Loop to Rule Them All"。

![](https://mmbiz.qpic.cn/sz_mmbiz_jpg/XW0OS1TIfjKBIEQof3N29Hy5qwZ7iaRQOdebJn3B2UfJ062Gr5pe9Xl466lZpz2wpmCNDWuHySTxJL8wxjwx4rRKHkrncDJ2iaz5Ou9IyuKHU/640?from=appmsg&watermark=1#imgIndex=2)

Agent核心循环

**第二章：启动流程与初始化**

分析了命令行入口点和系统初始化过程。从你在终端敲下 `claude` 那一刻开始，程序经历了哪些步骤才进入就绪状态——配置加载、环境检测、API连接建立、工具注册等。

**第三章：工具系统——Agent的"手脚"**

这可能是整个教程中信息密度最高的一章。Claude Code内建了**40多个工具**，每个功能——文件读写、Bash执行、Web抓取、LSP集成、浏览器操控——都是一个独立的、带权限控制的工具模块。

光是工具的基础定义就有29000行TypeScript。教程深入分析了工具注册机制、权限模型、输入输出schema设计。

更值得注意的是，多Agent协作功能（TeamCreate、SendMessage、ListPeers等）不是通过外部编排框架实现的——**它直接内建在工具系统里**。这是一个很有启发性的设计决策。

![](https://mmbiz.qpic.cn/mmbiz_jpg/XW0OS1TIfjIoZuLLe857rwELhI1MnPP0VmcnwAHX1PTaApch129ibajiaLxwNhw5Wd9fILvm9j1FQKGVaXhq6B4RnzYlzRLWHpK70GZgAoQB4/640?from=appmsg&watermark=1#imgIndex=3)

工具系统架构图

**第四章：对话管理与上下文工程**

Agent的核心挑战之一：如何在有限的上下文窗口中维持长时间的工作会话？

Claude Code的答案是**多层次记忆系统**：

*   ●**短期记忆**：当前会话的完整上下文

*   ●**中期记忆**：8段式结构化摘要，压缩比约20%

*   ●**长期记忆**：持久化到CLAUDE.md文件，跨会话存活

系统在上下文使用率达到92%时自动触发压缩，配合渐进式警告机制，确保不会因为上下文溢出而丢失关键信息。

> 这套记忆管理方案，本质上解决的是"如何让AI在8小时的编程马拉松中不忘记前3小时做了什么"这个工程难题。

**第五章：核心引擎——查询与流式执行**

深入分析了Agent的"大脑"是如何工作的：查询操作的生命周期、流式响应的处理、并行工具调用的编排。这里大量使用了async generators构建数据管道——一种非常优雅的流式处理模式。

![](https://mmbiz.qpic.cn/mmbiz_jpg/XW0OS1TIfjLWTQibictUkdicLznfnBbWXo0otgjgGdsB3pQVwd43Uib9ibQxqNtk7qe1mIcKYpoKhfvCicLFBSGrWs9jFNQODBgpfCzG4ichHgYVic4/640?from=appmsg&watermark=1#imgIndex=4)

记忆管理与流式执行

**第六章：安全机制**

一个在你电脑上能执行任意命令的AI，安全设计至关重要。这一章分析了Claude Code的权限系统、用户确认机制、沙箱策略。每个工具调用都经过权限检查，危险操作需要用户显式确认。

**第七章：可扩展性——Skills、插件与MCP**

Claude Code不是铁板一块，它通过三个层次实现可扩展性：

*   ●**Skills**（技能）：Markdown格式的能力描述，按需加载

*   ●**Plugins**（插件）：更重量级的功能扩展

*   ●**MCP协议**：连接外部工具和服务的标准接口

教程详细分析了每种扩展机制的设计哲学和实现细节。

**第八章：实战——从零构建一个简化版Code Agent**

最后一章是全书的高潮：**手把手带你实现一个能工作的简化版Code Agent**。

不是Hello World级别的玩具，而是一个真正能读文件、执行命令、与LLM交互的迷你Agent——用最少的代码重现Claude Code的核心架构。

![](https://mmbiz.qpic.cn/mmbiz_jpg/XW0OS1TIfjJlJGDiczyORToAvkydTBsCsZZ8CNTfdY2Irb3N7ez5DNqQvkdnXZW17uxZLtThYzC6ic1Rwn2h8E93nCg9NibApjViaicrMTVZ4UDs/640?from=appmsg&watermark=1#imgIndex=5)

从理论到实战

几个让我印象深刻的技术发现
-------------

通读教程后，有几个技术细节特别值得分享：

**React + Ink的终端UI方案**

Claude Code用React和Ink来渲染终端界面。对，你没看错——命令行里的每一个交互元素，本质上都是一棵React组件树。这让复杂的终端UI开发变得像写Web组件一样可维护。

**"One Loop to Rule Them All"的架构哲学**

不管Agent看起来多复杂，其核心永远是一个循环：

while (not done) {
    response = LLM(context + tools)
    if response.has\_tool\_calls:
        results = execute(tool\_calls)
        context.append(results)
    else:
        done = true
}

所有的复杂性——流式处理、并行执行、错误恢复——都是在这个基础循环上的工程优化。

**工具即能力的设计理念**

Claude Code的能力边界完全由工具决定。它不需要"理解"文件系统是什么——它只需要有一个FileRead工具和一个FileWrite工具。这种设计让能力扩展变得极其简单：想让Agent能做新事情？加个工具就行。

> 这也解释了为什么Claude Code能如此快速地迭代新功能——每个新能力都是一个独立的工具模块，互不干扰。

谁适合学这个教程？
---------

教程本身定位很明确：

*   ●想理解Agent架构的开发者——不是理论架构，是经过生产验证的真实架构

*   ●想深入了解Claude Code内部工作原理的用户

*   ●想自己构建Code Agent或类似工具的创业者

*   ●对LLM应用中的工具调用、Agent Loop等模式感兴趣的技术人

**前置知识要求不高**：熟悉TypeScript、了解基本的LLM API调用即可。教程会从头解释所有核心概念。

写在最后
----

Claude Code源码泄露是一次安全事故，但也意外地创造了一个独特的学习机会。

过去，想要理解一个工业级AI产品的内部架构，你只能靠官方博客里的蜻蜓点水、论文里的高度抽象、或者自己的逆向工程。现在，你有了51万行真实的生产代码，以及一套基于这些代码的系统化教程。

**build-code-agent** 项目的意义不仅在于它记录了Claude Code的技术细节，更在于它提炼出了一套**可迁移的Agent构建方法论**。不管你用的是Claude、GPT还是开源模型，Agent架构的核心挑战是相同的：如何设计工具系统、如何管理上下文、如何处理并发、如何保证安全。

项目地址：**github.com/jiji262/build-code-agent**，CC BY-NC-SA 4.0许可，欢迎Star和Fork。

如果你也在构建自己的Agent，这份教程值得通读。毕竟，能从一个价值数百亿美元的产品源码中学习架构设计的机会，不是天天都有的。