# 迁移 Blog 到 Astro | 新世界的大门
迁移 Blog 到 Astro | 新世界的大门

![](https://blog.xinshijiededa.men/logo.svg)

那些无法赞美的东西赞美着世界

1.  [  主页 / Home  ](/)
2.  [  归档 / Archives  ](/archives)
3.  [  友链 / Friends  ](/friends)
4.  [  订阅 / RSS  ](/atom.xml)
5.  [  关于 / About  ](/about)

![](https://user-images.githubusercontent.com/20166026/252788558-077bd50e-62c8-49ed-936f-2abfdf4b401d.jpg)

迁移 Blog 到 Astro
===============

日期：2023/8/31

分类： [Changelog](/categories/Changelog/)[页面仔的自我修养](/categories/页面仔的自我修养/)

标签： [Astro](/tags/Astro/)

为什么要迁移
------

我一直在使用 [Hexo](https://hexo.io/) 作为我的博客框架。但是 Hexo 有一些问题：

*   Hexo 的插件生态不够完善，很多插件都是半死不活的状态。
*   我用的 NeXT 主题中动画是采用 JavaScript 实现的，现在来说 CSS 已经足够。2023 年了，一篇（没有什么水平的）文章需要什么 Javascipt？
*   Hexo 称不上是一个现代的 SSG 框架。比如它没有 bundler，即使只用了几个 Font Awesome 图标，也要加载整个 stylesheet。
*   2023 年了，Hexo 还是没有热重载，每次修改完文章都要刷新页面，这个体验真的很差。

上面这些原因都是小问题。最大的问题在于 Hexo 很难注入自定义代码。比如我想写一个自定义组件，用来显示我的满文文章，我必须把文章的内容包在两层嵌套的 `<div>` 里面，才能让文字方向正确。这样做的问题是什么呢？

首先，这与 Markdown 标记文本是不统一的。如果我想要在上述的满文文章中插入一个链接，我必须在 Markdown 中写 `<a>` 标签，而不是写 Markdown 的链接语法。凭什么我要在 Markdown 中缝合 HTML 呢？

其次，这样做不符合语义化，而且可维护性很差。如果我想要修改这个自定义组件的样式，我很可能要同时修改所有 Markdown 中嵌套的两层 HTML，这样很容易出错。

我不想一下子就把所有的文章都迁移到 Astro，所以我决定渐进式迁移。所以起初我只将部分新的 Markdown 不足以完成需求的文章用 Astro 写，而且采用了一种很扭曲的方法：先渲染一次 Hexo，然后再将 Astro 渲染为 HTML，补上 frontmatter，将输出的文件复制到 Hexo 的 `source/_posts` 目录下当作 Markdown 文件，再经 Hexo 渲染为 HTML。不过，这样虽然能采用自定义的组件，但是构建时间长达十几秒。

几个月后，我终于无法忍受，将所有的文章都迁移到了 Astro。不过这相当于自己写一个网站了，非常耗时间，得全部写好才能发布。

在实际使用了几个月后，下面就是我对 Astro 的特性的一些评价。

Astro 的语法
---------

Astro 文件的标记语言跟 JSX 类似，但本质上区别很大。JSX 可以写在 JS 中，但 Astro 文件代码和页面结构分明，代码写在顶部的两行 `---` 之间，这部分的代码会在服务端渲染时执行。如果要在客户端执行，则需用 `<script>` 标签包裹，这被称为 client script。

Astro 并没有一套状态管理方法。绑定的变量值只在渲染阶段可变，一旦进入 HTML 就不可变了。这是因为 Astro 的 HTML 元素属性会被转成字符串。这样一来就也没有能绑定 onclick 之类事件的语法糖，你只能加一个 clilent script，然后在里面 `addEventListener()`。比较巧妙的一点是同一个组件在一个页面上多次出现，其 clilent script 也只会执行一次，所以对于大部分场景，你也不需要拿到当前组件的引用。

至于类似 JSX，`if` 只能使用三目运算符，我是觉得很恶心。好在 Astro 有丰富的 integration 生态和脱水机制，你可以选一个你喜欢的框架来写，比如 Svelte。

不过，Astro 自己语法的 compiler 有点问题，`<=` 被 tokenize 成了 `<Fragment>` 标记。

![](https://blog.xinshijiededa.men/_astro/leq-not-fragment.a08a6179_Z1WJFOw.webp)

再加一层括号可以避免这个问题，但括号会被格式话掉，只能把两端反过来写 `>=`。六月的 [几](https://github.com/withastro/compiler/issues/762#issuecomment-1649529196) [个](https://github.com/withastro/compiler/issues/723) [issue](https://github.com/withastro/astro/issues/6979)，今天还没修好……

路由
--

Astro 称自己的路由为“文件路由”，即每个文件都对应一个路由。这样做当然很直观，但是对我来说就很痛苦了。Astro 的示例中的博客文章统一放在 `/posts` 下，但是我的文章页面是直接放在根目录的。我不想把所有的文章都放在 `/posts` 下，因为这样会导致我的文章链接发生变化，而且发在其他地方也不直观。

Astro 2.0 支持了 content collection，目的是将渲染时不同类型的文章页面分类，这在一定程度上解决了我的问题。我只要创建一个 `[...slug].astro`，就可以接管 `pages` 内不匹配其他任何文件的路径了。这跟 SvelteKit 很像。Astro 由于要 SSG，还需要自己写一个函数提供所有可能的 slug 才能在构建时生成所有的 HTML 文件。

不过这个文件路由也是问题重重。`pages` 和 `content` 中所有的 html、astro、md、mdx 文件都会被尝试渲染。如果你想放一个其他类型的文件，Astro 会有不支持的文件类型的警告，需要在前面加 `_` 阻止其输出。但是我在 content collection 遇到了问题，我提了一个 [issue](https://github.com/withastro/astro/issues/7606)：

> Files with the _ prefix won’t be excluded and appear in the result of `getCollection`. However, accessing them will cause an error.
> 
> Create a \_folder in a collection with markdown files. The docs say “Files with the \_ prefix won’t be recognized by the router and won’t be placed into the dist/ directory”. If folders are expected to not exclude files, then accessing both of them raises an error. If folders are expected to work with underscores, then the two posts show up in the result of `getCollection`.
> 
> ![](https://github.com/withastro/astro/assets/20166026/2423822b-34fb-4a6a-aa52-ea4624403a29)
> 
> demo
> 
> ### Link to Minimal Reproducible Example
> 
> [https://stackblitz.com/edit/github-lhq8uj](https://stackblitz.com/edit/github-lhq8uj)

不过这个问题很快就 [被修](https://github.com/withastro/astro/pull/7611) 了，是一个 maintainer 自己改坏了。尝试 debug 的时候还 debug 到了 content collection 的 typegen 部分，虽然找到了问题的根源但是也没看懂。

```
diff --git a/packages/astro/src/content/vite-plugin-content-virtual-mod.ts b/packages/astro/src/content/vite-plugin-content-virtual-mod.ts
index 62ba612e962e..021a26314b72 100644
--- a/packages/astro/src/content/vite-plugin-content-virtual-mod.ts
+++ b/packages/astro/src/content/vite-plugin-content-virtual-mod.ts
@@ -213,7 +213,7 @@ function globWithUnderscoresIgnored(relContentDir: string, exts: string[]): stri
 	const contentDir = appendForwardSlash(relContentDir);
 	return [
 		`${contentDir}**/*${extGlob}`,
-		`!${contentDir}_*/**${extGlob}`,
-		`!${contentDir}_*${extGlob}`,
+		`!${contentDir}**/_*/**${extGlob}`,
+		`!${contentDir}**/_*${extGlob}`,
 	];
 }
```

图片优化
----

今天发布的 Astro 3.0 提供了一个 `<Image>` 组件，采用 Sharp 优化图片。

在 Astro 3.0 前，图片若放在 Markdown 文件同目录下，则需要用 ESM `import` 语法导入并且使用 `<Image>` 组件，无法使用 Markdown 的语法。所以我把它们都放在了 `public` 文件夹中，路径与文章相对 website root 的绝对路径一致。这样，我在 `src/content/blog/some-article.md`（渲染后的路径为 `/some-article.md`）中写 `![](./some-image.jpg)` 就可以使用 `public/some-article/some-image.jpg` 了。在 3.0 后，`![](./some-image.jpg)` 会导入 `src/content/blog/some-image.jpg`。所以我把文章放到了 `src/content/blog/some-article/index.md`，图片放在 `src/content/blog/some-article/some-image.jpg`。

在 Astro 2.0 加入了 content collection 后，我们可以写一个 `config.ts` 来用 `Zod` 声明所有集合的 frontmatter 类型。这确实是一个很好的功能，方便你在生成文章列表的场合不会出问题。Astro 还提供了 frontmatter 的 Zod 类型，看上去不错, 对吧？

所以，我想在 frontmatter 中使用 `image()` 来提升首页的加载速度。一切都很顺利，直到我修改到 [Open Graph](https://ogp.me/) 的部分。

在使用 `astro:assets` 之前，我会指定远程资源的URL。但是在 Astro 中，无论如何都无法加载远程图片，可能是由于代理设置的原因。`Image` 对象里只有类似 `"@fs/E:/blog"` 的路径，也没办法裁剪路径，因为输出的图像名称中包含哈希值。而且大部分的链接预览（比如 Telegram）都只支持 jpg / png / gif，不支持 webp 等，需要确保提供的图片的格式。

我将这些图片移动到`src`目录中后，发现只能使用 `<Image>` 组件来显示它们。当我尝试使用 `getImage()` 时，会抛出一个错误：

```
`Expected 'src' property to be either an ESM imported image or a string with the path of a remote image. Received 'undefined'.`
```

Astro 文档中说，如果你需要一个 asset 的直链，那还是使用 `public` 文件夹吧。[1](#user-content-fn-1)

我甚至还尝试在 Zod 中使用 `z.union([z.string(), image()])`，但是这样 Typescript 也没有办法正确地进行 type narrowing，类型还是不可用。看来不能两全其美了。

RSS 输出
------

最痛苦的一点是，Astro 虽然提供了 RSS 的 integration，但是想要输出全文内容居然要自己找一个 Markdown renderer 来渲染 Markdown。

如果是一个 `.astro` 文件，我可以通过在组件内部 import 一个 Astro 组件并用 `Astro.slots.render()` 获取其 slot 渲染后的 HTML，但是，在 `atom.xml.ts` 里的 API endpoint 中就不好办了。虽然我的 Astro 组件基本都是 noscript 的，但 Astro 中渲染 Markdown 实际上也是在渲染一个 component，需要保证安全性，所以没有实现。[2](#user-content-fn-2)所以现在本博客的 RSS 输出含 MDX 代码。

总结
--

Astro 的 SSG 和脱水机制的确很符合我的想法的。尽管有以上问题，Astro 作为一个 SSG first 框架，还是很适合 blog 这种静态站点的。**Blog 可以体现一个页面仔对于前端技术的一切追求，没有自己写一个 blog 的页面仔不是一个好的页面仔**。以上。

\-\-\-
------

1.  [Images 🚀 Astro Documentation # Where to store images](https://docs.astro.build/en/guides/images/#src-vs-public)。 [↩](#user-content-fnref-1)
    
2.  相关的 issue：[Container API: render components in isolation #533](https://github.com/withastro/roadmap/issues/533)。 [↩](#user-content-fnref-2)
    

本作品采用 **知识共享署名-非商业性使用 4.0 国际许可协议**（[CC BY-NC 4.0 International](https://creativecommons.org/licenses/by-nc/4.0/legalcode)） 进行许可。阁下可自由地**共享**（复制、发行）和**演绎**（修改、转换或二次创作）本作品，唯须遵守许可协议条款。

Built with [Astro](https://astro.build/)

Hosted & open sourced on [GitHub](https://github.com/OverflowCat/blog)

新世界的大門 2023
