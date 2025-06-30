# 2025-06-30-DOCKER 部署「Epub 小说」转「有声书」

对于听书党来说，喜马拉雅一直都是宝地般的存在，但是遇到没有人读的小说该怎么办呢？

去年，我还在烦恼 TTS 部署的麻烦，用来转换电子书要么就是只能在电脑操作，要么就是各种收费TTS，要么就是得挂科学，要么就是只能转换txt，或者转换以后没办法形成目录。

然而近期，我发现随着AI能力进一步提高，越来越多的电子书转换有声书的项目开始涌现，其中既有支持本地CPU/GPU跑的，也有支持 AI API 实现快速转换的，更有支持形成有声书元数据和目录的。

Today~ 咋们来分享一个免费、不花钱，而且跟知名有声书项目 AudiBookShelf 进行了深度结合的项目—— epub\_to\_audiobook 。□  [项目地址](https://github.com/p0n1/epub_to_audiobook) □ [部署教程](https://deepwiki.com/p0n1/epub_to_audiobook)

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMPj7cHrpx9J1I3qcw6xef8cFkeZYbBcVBPjlibZzGY8YDv3TBLrDds4Q/640?wx_fmt=png&from=appmsg)

* * *

首先我们准备一下项目文件夹。在个人空间任意位置创建一个文件夹，取名`epub2mp3`，当然你也可以自定义。然后在下面创建两个子文件夹`input`和`output`。

这里`input`代表待转换的电子书，`output`代表转换完成的有声书。这俩你也可以自定义，自己记住就行了。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMlgaZqseCmmVjKhkrKXq927On7GtAsXaqVWUELMA9dGfrUdQJCHmUeQ/640?wx_fmt=png&from=appmsg)

打开极空间`docker`应用，选择Compose标签，新建项目`epub2mp3`。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMc1jicQqv3MUA3mhnFpibzLIslCeiatwb5eu1eIfMKEgrhsXwiasp8iaeaBA/640?wx_fmt=png&from=appmsg)

把下面的代码复制到黑色框框里。

```bash
version: '3'
services:
  epub_to_audiobook:
    image: ghcr.io/p0n1/epub_to_audiobook:latest
    
    
      
      
      
      
      
      
      
    ports:
      - "7860:7860"
    volumes:
      - /路径/data:/app
    command: 'python3 /app_src/main_ui.py --host 0.0.0.0 --port 7860'
```

接着我们来修改这个compose.yaml代码，主要修改的就是`路径`。点击黑框框上方的`查询路径`按钮，复制`epub2mp3`文件夹所在的目录路径。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMu3WBXsvWpfxibj75xBzDGxK8sI6ml2CNrricCSvicM5C4Z8aJOibia9GI1w/640?wx_fmt=png&from=appmsg)

然后把复制下来的路径，替换代码中所有的【路径】中文，就和下图一样，然后创建。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMM5tjemn5xWwsYXiccXkk4Yw9Y6BpAZlibvxlGoTuibmEZcncgSbia8FFjdQ/640?wx_fmt=png&from=appmsg)

* * *

这个项目支持两种方式进行转换，**网页端**支持从PC上传电子书，也可以通过极空间内的浏览器访问NAS文件；**Cli模式**则是在NAS里进行转换，支持将NAS里的电子书直接输出为有声书。具体怎么用，就看我们的电子书存放在哪那里了。

1、网页端演示
-------

我们直接打开网页客户端，这里以极空间的浏览器应用为例。

首先我们把电子书上传到浏览器的极空间路径里备用。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMJNN9gz8vWjGWx1L48gI1GfPMBbUgl2ztbMxyIbm9Jw0M756AVpSWmw/640?wx_fmt=png&from=appmsg)

接着打开浏览器应用，输入该项目的URL地址，一般是`极空间IP:7860`。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMRqytk6PazyHr24DG793icewTNKuRJepl8TCTdW9EvicKFEuJGTvQeX7A/640?wx_fmt=png&from=appmsg)

然后左上角，选择刚才我们准备好的`epub`格式电子书。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMI2mRt0WIHrbFXkMepgcAdWSQkvoia3Jf6cLXicjG2XNBroibu1h8VdOAA/640?wx_fmt=png&from=appmsg)

中间的位置，可以设置标题模式，建议自动。然后可以设置只转换部分章节。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMkNXeS4qbXwyxFp0Umz3SoOlDl0pt7WGU9Om83DaOMWOp943bNyib18A/640?wx_fmt=png&from=appmsg)

最下面的位置，可以选择 TTS 种类，建议选免费的Edge，然后将Language修改为`zh-CN`中文，喜欢台妹风格的也可以替换为`zh-TW`。选择好语言后，选择Voice，即播音员的嗓音。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMeWKLSIq91OKsXgz87QjviaXGOvXvZOE45yzMGBr6x3VDB4Hs06jpEOQ/640?wx_fmt=png&from=appmsg)

点击运行，下面会展示容器日志，如果没有的话可以刷新下网页。指令一旦发布，就会在后台运行，不用担心中断。在日志里，我们可以看到项目已经对电子书进行章节判断，然后调用edge进行语音输出。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMZLCpr3ENKBAdcK4wYj9iaAMArh0jMcjPfibm9gic5U1qsbhLd8aJXz1fw/640?wx_fmt=png&from=appmsg)

回到极空间个人空间里，可以看到输出好的语音已经在里面了，后续就可以搭配极空间有声读物应用一起使用。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMQFZtDfBDiaRGw23zl9lwH3gSeF3FAEtAqRzG4tFjoskJyjTjGzYMDEQ/640?wx_fmt=png&from=appmsg)

2、Cli 演示
--------

Cli 也是一样，我们先将`epub`文件放到刚才配置的input目录下。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMTDW901SHOc3aCJESr0NxzMCnDicBQCwnwyP858Q6rIRErkMia1XeoZQA/640?wx_fmt=png&from=appmsg)

然后到docker界面，选择对应容器，点击`SSH`。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMYqhMviaP5P9NLdVyypW04iauyQegPj0aLYPPPA4vL8jR9F1oiaAeiccnMA/640?wx_fmt=png&from=appmsg)

在`SSH`页面，输入Cli 指令开始转换。

**标准格式**

```bash
python3 /app_src/main.py 待转换文件名 转换后目录 
```

**1️⃣示例 1**： 使用 Edge TTS ，转换中文朗读，语音为zh-CN-YunxiNeural

```css
python3 /app_src/main.py /input/ShiNanZhiTu.epub /output --tts edge --language zh-CN --voice_name "zh-CN-YunxiNeural" 
```

```

```

**2️⃣示例 2**： 使用 Openai TTS ，转换中文朗读，只转换第5-第10章节，休息时间1500ms，

```css
python3 main.py "path/to/book.epub" "path/to/output/folder" --tts openai --language zh-CN --chapter_start 5 --chapter_end 10 --break_duration "1500" --instructions "" 
```

```

```

3、性能损耗
------

我转换了一本`1.4mb`大小，`18w`字的电子书，大约花费`20`分钟，生成电子书文件`17章`，`151.7MB`。

我使用的设备是极空间Z423标准版，采用R5-5625U处理器，6核12线程，在转换过程中，极空间的CPU和内存可以说是毫无波澜，性能稳定。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMrwib3U0Gv0dp9ia7uzFBic632lVWoqUHzje8OQmezH87F44ltpC9RwEpA/640?wx_fmt=png&from=appmsg)

* * *

完成小说的TTS转换以后，剩下的就是如何方便我们日常收听了。如果是极空间的用户，那么其官方自带的应用——有声读物，就是一个很不错的原则。

极空间有声读物支持PC端、APP端等常用客户端，支持创建播单并批量增加有声书。支持AAC、AIFF、APE、AU、FLAC、M4A、MMF、MP3、Opus、VOC、WAV、OGG、RA、DVF、TTA、DSF、DFF、DTS、WMA等格式，并逐步增加。  

![](https://mmbiz.qpic.cn/mmbiz_png/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMGwTgchzyibgsic23ShuDKqaAO37cpHR1FSHlw97wtbD29HPDXahGoURg/640?wx_fmt=png&from=appmsg)

当然，最舒服的还是得极空间的APP端了，配置好路径、播单以后，多平台同步的收听进度，以及顺畅的收听体验，加上自己选择的美妙音色，效果绝佳。  

![](https://mmbiz.qpic.cn/mmbiz_jpg/wA0rnAvSU9D523tb3bb5bugic6NOBfJMM5vbfvw3lWgG0tWf8NGFue76sHyic3AkVFytK577HMWKDeyegRDdRFQQ/640?wx_fmt=jpeg&from=appmsg)

通勤时候倍数播放，或者是晚上助眠定时都是支持的，相对来说功能还是十分齐全。唯一遗憾的就是有声书目前没有刮削功能，希望后续极空间可以跟进跟进。  

![](https://mmbiz.qpic.cn/mmbiz_jpg/wA0rnAvSU9D523tb3bb5bugic6NOBfJMMqBjY6OiaWeYsmsWM65wSQS4icaUVBtMp1y2tWMsXoVyl6FLru1Ot9AKg/640?wx_fmt=jpeg&from=appmsg)

* * *

这个项目，可以说是我目前找到部署最简单，效果最好的电子书转有声书项目了。有需要的朋友，可以按照自己的喜好，快速将手头上想看的电子书转换成有声书，哪怕在冷门的小说，也可以通过AI一键转换，并且支持分章节导出。

搭配极空间APP，或者是 Audiobookshelf APP，都可以很好的实现有声书收听体验，真正让 AI NAS 除了在存储之外，增加一些日常可用的服务内容，更能省下一笔会员费用，给自己添一杯奶茶~

— 以上 —