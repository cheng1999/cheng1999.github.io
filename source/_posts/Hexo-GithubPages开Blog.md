---
title: Hexo 和 Github Pages 开 Blog (1)
date: 2016-11-04 21:10:26
tags:
  - 有点难度
categories:
  - 电脑
---
Github 有一个 Github Pages 的功能。
这个文章简单说明如何用 Hexo 在 Github Pages 上弄博客。

<!-- more -->

## 前言
为什么我开 Blog ?
- **首先**: 用了 Github Education Pack 架设了一个 Server 不知道做什么来于是弄了 {% link 一个 http://cheng1999.tk/wp/ %} 随便玩玩的 ~~(有了钱就是任性)~~。
- **后来**: 刚开始只是想试试看 Github Pages 的功能，
- **然后**: 就不小心开始弄 Blog 了。

弄 Blog 可以装逼，让外行人看到你有多厉害。~~也让厉害的人看你有多烂~~
再来就是看起来比较高级的学习笔记啦哈哈哈。
可以先跳到底部看一个 <a href="#后记">小故事</a>

这个文章分俩部分(俩篇)，第一篇主要关于 Hexo 的使用，第二篇才是关于 Github Pages 的。
而最终目的是使用 Github Pages 来 host 自己的博客。

## 一些基础要求
- Git 操作
- 懂一点网页开发
- 懂一点nodejs
- Markdown (这个很容易)

## 什么是 Hexo
**官方上是这样写**:
> A fast, simple & powerful blog framework

一个快速，简单 和 强大 的博客框架。我也是如此认为的。

## 使用 Hexo
Github 官方使用 Jekyll，而且内部直接 host 的。
如果你在 Hexo 和 Jekyll 间犹豫了，可以先照着做试试看 Hexo，因为步骤不多很简单。

可是为什么我不要用 Jekyll？那些主题真丑，可是自己又弄不出来....

- Hexo 是华人(台湾人)开发的
- 可以同时部署多个平台
- 比起用 Ruby 写的 Jekyll…… Javascript friendly
- 速度快
- 主题很多都比较漂亮的

### 开始
```bash
$ sudo npm install -g hexo-cli # 用 npm 安装 hexo
$ hexo init "blog" #创建 Hexo 博客目录
$ cd blog
$ npm install # npm 安装需要的包
$ hexo server # 开服务器可以预览
```
然后你可以用浏览器访问 `127.0.0.1:4000` 来看看用这五行命令生成的页面。

### 写第一个文章
```bash
$ hexo new "article's title"
```
然后对目录下 `source/_posts/` 的 Markdown 文件进行编辑，随便写写什么然后开浏览器直接预览，不需要重启 Hexo。
Hexo 的一个文章的 Markdown 文件前面还需要一些头设置，自动生成的话它也会自己加入这些内容。
![头示范](/images/hexo_postmd_head.png)
如果不会用 Markdown 的话没关系，它的学习成本很低，简单好用。
这里有一个 Cheatsheet : <https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet>

### 作出选择
到这里你可以说试用完成了，做出选择吧。
- **No**: 不开心的话就把 Hexo 的卸载掉吧！
```bash
$ sudo npm uninstall -g hexo-cli # npm 卸载
$ cd ..; rm -rf "blog" # 删除掉 Hexo 博客目录
```
- **Yes**: 继续往下看
如果对 Hexo 有更多兴趣的话，应该去官网看文档，文章接下去的内容比较多是官方文档缺少的。
**官网**: https://hexo.io/

## Hexo 配置建议
### 站点设置
首先最重要的就是去目录下`_config.yml`做你的配置，照着填就对了。

### 主题
我用的是 Jacman
**安装**:
其它的主题也类似这样
```bash
$ git clone https://github.com/wuchong/jacman.git themes/jacman
```
更改`_config.yml`的 theme 配置。
```
theme: jacman
```
然后重新开 Hexo，开浏览器去看看效果。
选定的 theme 要去看关于 theme 的文档，看看怎么配置怎么使用的。一般上 theme 目录下还有 `_config.yml` 等着你去设置。

### 几个好用的插件
- **Rss 订阅**:
```bash
$ npm install hexo-generator-feed --save # 给博客安装插件
$ hexo generate # 让 atom.xml 文件的生成
```
生成了 atom.xml，别人可以通过 Rss 订阅你的博客。

- **Sitemap**:
```bash
$ npm install hexo-generator-sitemap --save
$ hexo generate
```
生成 sitemap.xml，站点地图。
如过你有用 Google Search Console 会话会需要到这个。

### 其它
这个部分很懒惰写了，具体自己 Google 脑补。
- **Google Analytics**
很好用的 Google webmaster tools，可以分析站点的数据。
- **Google Search**
让你的网站被 Crawled, Indexed。在 Google 上能被搜索的到。

## 后记
从前从前(俩年前)，
班上的 许善旻同学 在我的诱骗下也用了 Github Pages，而且纯手工自己产代码哦！~~(挺勤奋挺傻的)~~
附上几个 link:
- <https://oscarhii.github.io/chs%20web/home.html>
- <https://oscarhii.github.io/web%20new/home.html>
- <https://oscarhii.github.io/birthday.html>
*链接未经过他人同意被我嚣张擅自引用。*
