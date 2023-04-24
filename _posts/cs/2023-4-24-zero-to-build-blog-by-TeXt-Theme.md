---
title: 从零搭建TeXt Theme
key: zero-to-build-blog-by-TeXt-Theme
tags: ["TeXt", "Blog build"]
modify_date: "2023-04-24 21:48:00"
article_header:
aside:
    toc: true
---

今天听群友聊到建站，恰巧看到了TeXT项目，于是进行一个搭的建

## 下载与配置

注意：本教程基于配置于github上的github page建站（就是用Github做服务器啦）

首先，先创建一个类似于 `\{{用户名\}}.github.io`的仓库

然后git clone下[TeXT项目](https://github.com/kitian616/jekyll-TeXt-theme)

`当然你也可以选择直接fork过来，但我觉得直接fork过来一更新自己的东西全无了(本质是自己太菜了) orz`

下载完成后，我们首先要了解到文件体系的架构：

- _posts 博客内容
- _pages 其他需要生成的网页，如About页
- _layouts 网页排版模板
- _includes 被模板包含的HTML片段
- _data 动态数据
- _sites 最终生成的静态网页
- _config.yml 网站的一些配置信息，在此处修改位置assets 辅助资源 css布局 js脚本 图片等
- index.html 网站的入口

由上述架构可知，我们主要配置博客信息的地方在于**_config.yml**，并在**_posts**文件夹下写博客(markdown格式)

<img src="img/cs/image-20230424204450251.png" alt="image-20230424204450251" />

<center><font size ='2'>没错就是这俩倒霉蛋</font></center>

一般我们要在`_config.yml`内更改以下项：

- Site Settings (网页设置)
  - text_skin：想改主页样式可以在这里设置(https://kitian616.github.io/jekyll-TeXt-theme/docs/zh/configuration#皮肤)
  - title：不会有人不改Blog标题吧，不会吧不会吧（真的不会）
- author (博客所有者信息)
  - name：博客主名
  - bio：个人描述
  - email：你的email地址
  - github：github用户名（方便跳转到Github主页）
  - ...
- GitHub Repository（如果你的站点部署在Github上，那么这一点非常重要）
  - repository：填写你的仓库地址，就是那个`{{用户名}}.github.io`
  - repository_tree：仓库树，看准你的仓库推送位置（现在从master都变为main了）

p.s. 一个小问题在于，你需要到`_data\locale.yml`下更改你的Blog日期（不然会闹出Blog从过去产生的笑话） 



## 推送到github



(这里一度出现各类乱七八糟的问题，待填坑)





## 撰写博客

 

前文提到，**所有的文章都在 */_posts* 文件夹中**。这些文件可以用 Markdown 或 HTML 编写。只要文件中有 YAML 头信息，它们就会从源格式转化成 HTML 页面，从而成为你的静态网站的一部分。

### 创建文章

发表一篇新文章，你所需要做的就是在 */_posts* 文件夹中创建一个新的文件。文件名的命名非常重要。Jekyll 要求一篇文章的文件名遵循下面的格式：

```
年-月-日-标题.MARKUP
```

下面是一些合法的文件名的例子：

```
2011-12-31-new-years-eve-is-awesome.md
2012-09-12-how-to-write-a-blog.markdown
```

### 内容相关

所有博客文章顶部必须有一段 YAML 头信息(YAML front-matter)。

为了提高文章的阅读和书写体验，TeXt 在 Markdown 原有的基础上做了一些增强。

#### YAML 头信息

```
---
layout: article
title: Document - Writing Posts
mathjax: true
---
```

在 `---` 之间你可以设置属性的值，可以把它们看作页面的配置，这些配置会覆盖在 *_config.yml* 文件中设置的全局配置。

除去 Jekyll 自定义的变量外，TeXt 也定义了一些额外的变量，详情请戳[布局](https://tianqi.name/jekyll-TeXt-theme/docs/zh/layouts)。

