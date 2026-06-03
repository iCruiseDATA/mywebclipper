# 2026-06-03_OpenClaw多Agent协作踩坑实录
最近，我在折腾OpenClaw的多Agent团队协作功能，想搭建一个AI写作团队：运营主管阿强、研究员阿亮、写手阿文、审核员阿严，4个Bot协作写文章。

想法很美好，现实很骨感。配置过程中踩了一堆坑，一度怀疑人生。今天把这趟"翻车-爬起-跑通"的全过程分享给你，帮你避开这些坑。

* * *

一、先说说我要做什么
----------

简单来说，就是**只跟阿强说话**，让他自动协调其他三个Bot完成文章写作： ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220194329904.png)

听起来很酷对吧？但配置过程让我差点放弃。

* * *

二、踩坑实录
------

### 坑1：跨Agent通信权限没开（最隐蔽的坑）

**现象**： 阿强收到任务后，只说"好的，我立即协调团队"，然后就没下文了。其他Bot一点反应都没有。

查日志发现报错：

```ini
需要设置 tools.sessions.visibility=all 才能向其他团队成员发送消息

```

**原因**： `openclaw.json` 里缺了一个关键配置。默认情况下，Agent只能看到自己的会话，看不到其他Bot的会话。

**解决方案**： 在 `openclaw.json` 的 `tools` 部分添加：

```json
"tools": {
  "sessions": {
    "visibility": "all"
  }
}

```

**经验教训**： 这个配置在官方文档里有，但很多教程没强调。没有它，多Agent协作根本玩不起来。

* * *

### 坑2：文件路径错乱（最折腾的坑）

**现象**： 阿亮说大纲已经保存了，阿文却说找不到文件。

查看日志发现搞笑的一幕：

```ruby
阿亮保存到：~/.openclaw/workspace/openclaw-camp-article/outline.md
阿文去读取：~/.openclaw/agents/writer/workspace/workspace/openclaw-camp-article/outline.md

```

注意看，阿文的路径里多了个 `workspace/workspace`，变成嵌套路径了！

**原因**： 每个Agent有自己的 `workspace` 目录，但我让阿亮保存文件时用了相对路径 `workspace/...`，不同Agent解析出来路径不一致。

**解决方案**： 所有Agent共享的文件，必须用**绝对路径**：

```css
~/.openclaw/workspace/openclaw-camp-article/outline.md

```

而不是相对路径：

```css
workspace/openclaw-camp-article/outline.md

```

**经验教训**： SOUL.md里所有的文件路径都要用 `~/.openclaw/workspace/...` 开头，确保大家都能找到同一个文件。

* * *

### 坑3：agentToAgent.allow配错了（最无语的坑）

**现象**： 想开启Agent间直接通信，配置了 `agentToAgent`，但一直不生效。

**错误配置**：

```json
"agentToAgent": {
  "enabled": true,
  "allow": ["sessions_list", "sessions_send", "sessions_history"]
}

```

看出来问题了吗？我把**工具名**填进去了！

**正确配置**：

```json
"agentToAgent": {
  "enabled": true,
  "allow": ["manager", "researcher", "writer", "reviewer"]
}

```

`allow` 里应该填的是**Agent的ID**，不是工具名！

**经验教训**： 配置项的命名容易误导。`allow`指的是"允许哪些Agent之间通信"，不是"允许使用哪些工具"。

* * *

### 坑4：全局tools.deny误伤友军（最坑的坑）

**现象**： 我在 `openclaw.json` 根目录配置了全局限制：

```json
"tools": {
  "deny": ["write", "edit", "exec", "apply_patch"]
}

```

想着限制一下阿强的写入权限，结果**所有Agent都不能写文件了**！阿文连文章都保存不了。

**原因**： `tools.deny` 放在根目录会影响所有Agent。想单独限制某个Agent，要在该Agent的配置里加：

```json
{
  "id": "manager",
  "name": "阿强",
  "tools": {
    "allow": ["sessions_list", "sessions_send", "sessions_history", "read"],
    "deny": ["write", "edit", "exec", "apply_patch", "bash"]
  }
}

```

**经验教训**： 权限控制要精确到Agent级别，不要搞全局限制，否则连自己一起坑。

* * *

### 坑5：以为能看到所有Bot的回复（最天真的坑）

**现象**： 我傻傻地以为配置了4个Bot，就能看到4个窗口同时聊天。结果只收到阿强的回复，其他Bot好像"消失"了。

**真相**： 这是正常的！`sessions_send` 的工作方式就是**后台通信**。

阿强用 `sessions_send` 发消息给阿亮，阿亮在后台会话里处理，回复也是直接给阿强，不是给你。

你能看到的只有阿强的汇总结果，其他Bot的对话过程在后台"一闪而过"。

**解决方案**： 如果想要"过程清晰可见"，需要用 `sessions_spawn`（子智能体）方式，这个在后续教程里会讲。

**经验教训**： 不要以为是配置错了，这只是不同协调方式的特性差异。

* * *

三、跑通后的效果
--------

搞定所有坑之后，效果是这样的：

**我给阿强发消息**：

```diff
你好，我需要写一篇介绍OpenClaw的文章
要求：
- 主题：OpenClaw是什么，为什么现在这么火
- 目标读者：零基础小白
- 字数：2000左右
- 风格：通俗易懂

请协调团队完成。

```

**阿强回复**（约10分钟后）：

```css
✅ 任务完成！

📊 执行摘要：
阶段1：资料搜集（阿亮）- 已完成
阶段2：撰写初稿（阿文）- 已完成
阶段3：质量审核（阿严）- 已完成
阶段4：修改定稿（阿文）- 已完成

📁 成果文件：
- 终稿：~/.openclaw/workspace/openclaw-camp-article/final.md

[文章内容...]

```

所有中间产物（大纲、初稿、审核报告）都保存在共享目录里，想看随时能看。

以下是过程实录：

##### 1、给阿强下达任务需求

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220171347165.png)

##### 2、研究员-阿亮收到任务

阿亮收到任务开始干活，然后将交付物，转给写手-阿文。 ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220171608426.png)

##### 3、写手-阿文收到任务

先是收到了阿强给的任务，先读取风格指南，等待阿亮的大纲。 ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220172250003.png)

等到阿亮的大纲，开始干活，完成后转交给审核员-阿严来审核 ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220172411698.png)

##### 4、审核员-阿严收到写手-阿亮的文章

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220172745512.png)

##### 5、写手-阿文收到阿言的审核意见，开始优化

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220172955399.png)

##### 6、运营主管-阿强收到所有成员的进展状态已完成

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220173147868.png)

##### 7、我收到阿强的汇报消息

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220173307154.png)

##### 8、协作过程中产生的会话记录

每个bot都由sessions记录产生，证明协作过程中间他们是有通话记录的，感兴趣的可以点击进去看一下会话记录。

![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260220175011571.png)

以上只是一个团队协作的雏形，后续改造成子 Agent 协作，过程会更直观，灵活性会更高！

四、核心配置清单
--------

如果你也想搭一个，这里是**经过验证的完整配置**：

### 1\. openclaw.json 关键部分

```json
{
  "agents": {
    "list": [
      {
        "id": "manager",
        "name": "阿强",
        "workspace": "~/.openclaw/agents/manager/workspace",
        "agentDir": "~/.openclaw/agents/manager/agent",
        "tools": {
          "allow": ["sessions_list", "sessions_send", "sessions_history", "read"],
          "deny": ["write", "edit", "exec", "apply_patch", "bash"]
        }
      },
      {
        "id": "researcher",
        "name": "阿亮",
        "workspace": "~/.openclaw/agents/researcher/workspace",
        "agentDir": "~/.openclaw/agents/researcher/agent"
      },
      {
        "id": "writer",
        "name": "阿文",
        "workspace": "~/.openclaw/agents/writer/workspace",
        "agentDir": "~/.openclaw/agents/writer/agent"
      },
      {
        "id": "reviewer",
        "name": "阿严",
        "workspace": "~/.openclaw/agents/reviewer/workspace",
        "agentDir": "~/.openclaw/agents/reviewer/agent"
      }
    ]
  },
  "bindings": [
    {
      "agentId": "manager",
      "match": { "channel": "telegram", "accountId": "manager" }
    },
    {
      "agentId": "researcher",
      "match": { "channel": "telegram", "accountId": "researcher" }
    },
    {
      "agentId": "writer",
      "match": { "channel": "telegram", "accountId": "writer" }
    },
    {
      "agentId": "reviewer",
      "match": { "channel": "telegram", "accountId": "reviewer" }
    }
  ],
  "tools": {
    "sessions": {
      "visibility": "all"
    }
  }
}

```

### 2\. SOUL.md 文件路径规范

所有文件路径都用**绝对路径**：

```markdown
- 大纲：~/.openclaw/workspace/openclaw-camp-article/outline.md
- 初稿：~/.openclaw/workspace/openclaw-camp-article/draft-v1.md
- 审核报告：~/.openclaw/workspace/openclaw-camp-article/review-v1.md
- 终稿：~/.openclaw/workspace/openclaw-camp-article/final.md

```

### ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/md/20260219223904633.png)

五、小结
----

这趟踩坑之旅让我明白了几件事：

1.  **文档要看全**：`tools.sessions.visibility` 这种关键配置，很多教程一笔带过
2.  **路径要用绝对**：相对路径在多Agent场景下就是定时炸弹
3.  **配置要精确**：Agent级别的配置别放全局，否则影响所有Bot
4.  **预期要对齐**：`sessions_send` 就是"后台协作"模式，看不到过程是正常的

现在我的AI写作团队已经能正常工作了。从给阿强下达任务到拿到终稿，全程约10分钟，比我一个人折腾要快得多。

如果你也在玩OpenClaw多Agent，希望这篇踩坑记录能帮你少走弯路。

* * *

六、想系统学习OpenClaw？
----------------

如果你对OpenClaw感兴趣，想从零开始搭建自己的AI团队，欢迎加入我们的**OpenClaw训练营**。

**你能学到什么**：

*   OpenClaw基础配置与进阶技巧
*   多Agent团队协作的三种实现方式
*   搭建自己的AI内容创作团队
*   自动化工作流实战案例

**适合人群**：

*   想提升效率的职场人
*   对AI自动化感兴趣的开发者
*   想搭建个人AI助手的内容创作者

点击下方海报了解详情 👇 ![](https://wamplempic.oss-cn-beijing.aliyuncs.com/mdimage-20260220204849728.png)

* * *

_我是阿坡(v ao-ai-coding)，专注于AI提效实战。有问题欢迎评论区留言！_