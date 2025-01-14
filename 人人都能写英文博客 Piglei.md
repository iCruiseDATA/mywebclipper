# 人人都能写英文博客 | Piglei
时间过得很快，转眼间，2024 年的进度条已经走到了 50% 的位置。作为一名博主，我很惭愧 🥹，过去半年我只写了[一篇新文章](https://www.piglei.com/articles/three-little-things-on-code-review/)，算是相当低产。不过，虽然没写太多新文章，但我干了另一件值得记录的大事。

在今年 2 月份，我给博客增加了[“英文”板块](https://www.piglei.com/en/)，并在其中发表了 4 篇英文文章，几乎每一篇都获得了不错的反响：

1.  _["After 14 years in the industry, I still find programming difficult"](https://www.piglei.com/articles/en-programming-is-still-hard-after-14-years/)_：[Hacker News](https://news.ycombinator.com/item?id=39480605) 217 points(**Top 20**) 评论数 190+，[reddit r/programming](https://www.reddit.com/r/programming/comments/1ay0ik5/after_14_years_in_the_industry_i_still_find/) 773 votes(**Top 1**) 评论数 310+，被翻译成[俄语](https://habr.com/ru/articles/795933/)、韩语
2.  _["6 ways to improve the architecture of your Python project (using import-linter)"](https://www.piglei.com/articles/en-6-ways-to-improve-the-arch-of-you-py-project/)_：登上 [PyCoder's Weekly 周刊](https://pycoders.com/issues/619)，被播客节目 [Python Bytes 推荐](https://www.youtube.com/watch?v=SaV3sJ8FlZU&t=189s&ab_channel=PythonBytesPodcast)，被 [Real Python 官方账号推荐](https://x.com/realpython/status/1788765963761992171)
3.  _["3 important things I overlooked during code reviews"](https://www.piglei.com/articles/3-important-things-I-overlooked-during-cr/)_：[reddit p/programming](https://www.reddit.com/r/programming/comments/1c7v8h4/3_important_things_i_overlooked_during_code/) 90 votes(**Top 5**)，评论数 16，[Lobster](https://lobste.rs/s/xlpjaz/3_important_things_i_overlooked_during) 21 votes 评论数 46

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_top1.png)

图：piglei.com 登上 Reddit /p/programming TOP1，并在上面停留了整整一天

简单来说，在阅读量和读者反馈方面，这些英文文章成绩斐然。并且在某些维度（比如评论数量）上的数据表现，远远超我所写过的任何一篇中文文章。

不过，也许现在屏幕前的你已经皱起了眉头，想说：_“行了，行了，piglei 你这个货别显摆了，现在我知道你英文很牛逼了，能写出流利的英文文章来，满意了吧！”_

先别急着下结论，其实我的英文能力非常普通（大学六级考两次的水平）。因此，这些文章其实也并非由我从零开始写就，或许眼尖的你已经发现，它们都是由我写过的中文文章翻译而来。

我借助了 GPT 4 和 DeepL Write 等先进工具完成了翻译，并尽全力保证译文“信雅达”，让它们读起来就像是出自一位熟练的英文写作者之手（此处有吹牛成分）。

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_comment.png)

图：一位读者表示“根本看不出来文章是由中文翻译而来”，incredible！

我使用的翻译方式没有什么门槛，任何一位中文写作者，都能用它来创作属于自己的英文文章。我将在本文教会你具体的方法。

但在进入正题前，让我们先把时钟往回拨一拨，回到今年的二月份，看看究竟是什么事情，在我心里埋下了想开始“英文写作”的种子。

### 开始“英文写作”的契机

二月份的某个周五，在用谷歌搜索资料时，我无意读到一篇关于 ChatGPT 的英文文章。不读不要紧，一读吓一跳，这篇文章的内容，根我在 2022 年写的一篇中文文章[《ChatGPT 正在杀死编程里的乐趣》](https://www.piglei.com/articles/chatgpt-and-how-we-programming/)一模一样。

然后，我顺藤摸瓜点进作者的主页，发现了更多源自我的博客 [piglei.com](https://www.piglei.com/) 的文章，比如《Python 工匠》系列，等等。

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_bo_leo.png)

图：名为 bo leo 用英文大量洗稿了我的博客文章

这些文章没有注明原始出处，作者 bo leo 也从未联系过我征求授权，明显侵犯了我身为原创作者的权益。于是，我在 Medium 平台上举报了这些文章，几个小时后，它们就被下线了（_也可能是被作者主动删除，因为事情在推特上被曝光_）。

这件事看似得到了圆满的解决，但我的心情却无法平静。因为在点开几篇翻译质量粗糙的“英文盗版文章”后，我在评论区发现了不少高质量的读者评论，部分观点极具启发性——若是它们出现在自己博客的正版文章的评论区，那该多好啊！

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_chatgpt.png)

图：《ChatGPT 正在杀死编程里的乐趣》英文盗版，右边的读者评论写得很棒

既然那么糟糕的英文版都能获得读者认可，假如翻译质量再好一点呢？再进一步，为什么要给这些偷偷洗稿的卑鄙小人可乘之机，为什么我不干脆自己动手，直接为每一篇自己的得意之作发布对应的“官方英文版”呢？

就这样，在一个月朗星稀的周五晚上，piglei 坐在笔记本电脑前，下决心开始自己的“英文写作”之路——当然，如果你非得要较真的话，他走上的并非真正意义上的“写作”之路，而是一条名为“LLM 英文翻译 + 工具润色”的捷径 😅。

### 用 LLM 翻译初稿

“机翻（机器翻译）”，在很长一段时间里都是“低质量翻译”的代名词。然而在 ChatGPT 3.5 等大语言模型横空出世后，“机翻”的质量跃升到了一个前所未有的高度。不论是在准确度、流畅度和专业名词翻译方面，优秀的大语言模型所生成的译文，几乎接近普通人类的翻译水准。

因此，我选择用 LLM 来完成译文的初稿。在模型方面，我用到了 OpenAI 的 GPT-4（通过 API 调用），你也可以用其他模型来替代。

为了尽量提升译文的质量，我编写了以下提示语（prompt）来帮助 GPT-4 更好地完成翻译：

```null
You are a professional English translator. I'll send you Chinese content, please translate it into American English.

Requirements:

- Correct any grammatical errors in the original content before translating it.
- The English version should use a concise, direct and clear writing style.
- The content may use markdown format, please keep the format as it is.

Respond only with the translated content.

```

之后的操作流程比较简单：把中文发给大模型，它就会吐给你一份英文。一篇文章的篇幅通常很长，你需要将其拆分为多个段落，分段完成翻译。

一些注意事项：

*   在翻译每个新的段落前，记得清空当前聊天的上下文，否则会被多收很多钱（按 token 计费时）
*   不同段落的译文，对同一个专业名词的翻译需保持一致
*   如果原文是 Markdown 格式，注意让译文维持原格式
*   如果原文中的书名或引用段落的原始语言就是英文，那就不要用 LLM 的译文，找到被引用内容的原始英文表达

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_gpt4_trans.png)

图：使用 GPT-4 翻译一个段落

这样重复执行多次“复制 -> 聊天 -> 粘贴”后，一篇由 LLM 完成的初稿便落到了我们的手中。

一眼看上去，初稿的翻译质量似乎已然十分出色（前提是使用的模型能力足够强大）。但是如果细读，还是会发现文本中藏着许多小瑕疵，值得进一步优化。因此，我建议继续对初稿实施二次校对和润色。

### 用 DeepL Write 润色

假如你的英文水平非常过硬，那么你可以直接自己动手来完成润色。但是，对于我这种英文半吊子来说，借助工具是更合适的选择。工具方面，我挑选了知名翻译网站 DeepL 出品的写作助手：[DeepL Write](https://www.deepl.com/en/write)。

DeepL Write 用起来很简单，只要把原文粘贴到左侧文本框，选择语言为 English，右侧便马上会出现优化过的版本。

![](https://www.piglei.com/static/uploaded/2024/07/write_eng_blog_deepl_demo.png)

图：DeepL Write 界面截图，右侧带下划线的文字是建议优化的内容

但是请注意，虽然 DeepL Write 工具会提供一些优化建议，但它们就像 LLM 的翻译一样——并非 100% 可靠。

所以，**作为唯一的人类创作者，我们仍需亲自决定每一个词语、每一种句式。**  也正是因为如此，在润色阶段，拥有优秀的英文语感非常重要，因为你要凭借这份语感，来判断哪种写法会给读者提供更优的阅读体验。

在培养语感方面，我认为长期阅读高质量英文文章很有帮助。

### 推广你的文章

万事俱备，只欠东风。有了英文文章后，下一步便是给它找到最匹配的读者群。幸运的是，在英文世界中推广自己的文章，比在中文世界要方便太多，大多数时候，你只需要轻点小手，把文章的 URL 提交到心仪的资讯站点即可。

目前，我尝试过以下几种渠道：

1.  [Hacker News](https://news.ycombinator.com/)：最知名的科技类资讯站点，流量巨大
2.  [Reddit r/programming](https://www.reddit.com/r/programming/)：知名的编程相关资讯节点，流量很大
3.  [Lobster](https://lobste.rs/)：流行的科技资讯站点，与 HN 风格类似，流量较大，技术讨论氛围非常好
4.  [PyCoder's Weekly](https://pycoders.com/)：知名 Python 编程语言周刊，订阅量巨大

除了以上渠道以外，你也可尝试一些契合文章调性的其他渠道，打个比方，一篇 Go 语言的技术文章，就很适合提交到 Reddit 的 [/r/golang](https://www.reddit.com/r/golang/) 节点上。

> ⚠️ 注意：虽说积极推广自己的文章不是什么坏事，但也请不要滥用。每次投稿前，请确保内容质量达到标准，并契合对应渠道的读者群。否则会讨人嫌哦！

### ❤️ 我喜欢这种创作模式

如你所见，我使用的“英文写作（翻译）”方式非常非常非常简单，似乎稍微有点脑子的人就能想到。但其实，在实际上手用 GPT-4 + DeepL 完成第一篇文章前，我的心情极度忐忑。我能听到心中有个小人不停小声念叨：_“机器翻译的文章，真的能让英文读者满意吗？”_

待到第一篇文章发布，收获了大量的正反馈后，我才敢真正确认，这确实是一条相当可行的创作模式。

我个人非常喜欢这种模式。**因为在这之前，我从未想过自己能用第二语言，写出被数万人喜爱的技术文章。**  即便这算不上“一字一句”完成的那种真正的写作，但当你读到最终的英文成品时，会发现无论从语言、节奏还是腔调上，它都同自己的创作灵魂契合得天衣无缝，让你满心欢喜。

### 结语

我花了整整三十年，才学会如何用自己的母语写出文通字顺的文章。假如，我从现在开始学习完全用英文写作，不知还得练习多少年，才能勉强达到及格线。但如今借助 LLM 等现代化工具，我轻松实现了自己的“英文写作梦”。

记得发布完第一篇英文文章后，深圳已经进入深夜，但因为时差原因，文章在 Reddit 和 Hacker News 的热度却在一路走高。看着 vote 数和评论数不断增长，我兴奋得完全无法入睡，几乎每隔三十分钟就要抓起手机，看一遍最新的访问数据。

后来几经辗转，终于进入了梦乡。我已经忘了那晚梦见了什么，但我能想起的是，第二天早晨醒来后，我感受到了一种就像是刚刚学会写字时的喜悦。

> 😊 如果你喜欢这篇文章，也欢迎了解我的书： **[《Python 工匠：案例、技巧与工程实践》](https://www.piglei.com/book/index.html)** 。它专注于编程基础素养与 Python 高级技巧的结合，是一本广受好评、适合许多人的 Python 进阶书。