---
title: Hexo 和 Github Pages 开 Blog (2)
date: 2016-11-05 18:14:57
tags:
  - 有点难度
categories:
  - 电脑
---
Github 有一个 Github Pages 的功能。
这个文章简单说明如何用 Hexo 在 Github Pages 上弄博客。

<!-- more -->

## 关于 Github Pages
<br><br>
{% youtube 2MsN8gpT6jY %}
### 优点
- 我觉得有逼格
- 相对稳定
- 免费

### 缺点
- 100GB 流量 or 100,000 requests
- 1GB 容量
- 静态网页，动态的功能要动用到外部的服务
这些限制对大部分人也太够了

## 简单的开始
如果这个不会你应该看不懂下面的内容了……

**第一步**: 创建 Repository
> 在 Github 上创建一个 repository，名字叫 ***username.github.io***。其中 ***username*** 就是你的用户名啦(阿废话阿)！

**第二步**: Git clone 下来。
```bash
$ git clone https://github.com/username/username.github.io
```

**第三步**: 创建文件
```bash
$ cd username.github.io
$ echo "Hello World" > index.html
```

**第四步**: Commit and Push
```bash
$ git add --all
$ git commit -m "Initial commit"
$ git push -u origin master
```

**第五步**: 访问 ***{%raw%} http://username.github.io {%endraw%}*** 。

> 如果你是针对一个项目来特别设立 Github Pages，就要在那个项目的 repository 下创建一个 Branch 名字叫 `gh-pages`。
> 这个 Page 的地址就是 ***{%raw%} http://username.github.io/repository-name {%endraw%}***。***repository-name*** 要填什么自己知道。

<a href="#后记">之前</a>说到 许善旻同学 纯手工产代码的故事就是在第三步的不停折腾……

## Hexo Github Pages 部署
终于到了这个部分，Hexo 是可以把博客部署到不同平台的。
怎么生成静态网页部署到 Github Pages 去 ?

<br>
### 建立 git 和 Github 的 SSH 访问通道
*参考*: <https://help.github.com/articles/generating-an-ssh-key/>
**第一步**: 生成 SSH key
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
**第二步**: 把 SSH key 加入 ssh-agent
- 就是把 SSH private key 交给 ssh-agent，这样其它程序需要 key 时可以向 ssh-agent 申请，我们这些懒人就可以不需要一直打密码了。

```bash
$ eval "$(ssh-agent -s)" # 开 ssh-agent
$ ssh-add ~/.ssh/id_rsa # 交 SSH private key 给 ssh-agent
```

**第三步**: 把 SSH key 加入 Github 账户
- 储存 public key 的文件 `~/.ssh/id_rsa.pub`，把里面的内容 copy出来。
- 去 Github > `Settings` > `SSH and GPG keys` > `New SSH key` > (填空位，paste public key) > `Add SSH Key`
> 也可以针对单个 Repository 来填加 SSH key

**第四步(可选)**: 测试和 Github 的连接，你足够自信可以跳过这个步骤。
```bash
$ ssh -T git@github.com
Hi cheng1999! You've successfully authenticated, but GitHub does not provide shell access.
```

<br>
### Hexo 部分
**第一步**: 配置 Deployment
编辑 `_config.yml`，去最后一行，配置示范如下:
```
deploy:
  type: git
  repo: git@github.com:cheng1999/cheng1999.github.io
  branch: master
```

**第二步**: DEPLOY!
```bash
$ hexo clean
$ hexo generate
$ hexo deploy # DEPLOY!
```

<br>
### 其它
Hexo Deploy 到 Github Pages 的方法其实就是生成静态网页，然后 push 到 Repository 上。因为 push 是 force 的，所以如果你把目录下的 `.deploy_git` 删掉再 `hexo deploy` 一次，Github 上的 Commit 会被 reset掉。

还有一个建议就是 Repository 可以创建另一个 branch 来放 Hexo 的目录。(master branch 是用来放部署的静态网页)。

## 后记
后记我还想再放这个:

> 班上的 许善旻同学 在我的诱骗下也用了 Github Pages，而且纯手工自己产代码哦！~~(挺勤奋挺傻的)~~
附上几个 link:
- <https://oscarhii.github.io/chs%20web/home.html>
- <https://oscarhii.github.io/web%20new/home.html>
- <https://oscarhii.github.io/birthday.html>
*链接未经过他人同意被我嚣张擅自引用。*


### 2018年更新
重温博客时发现没有教如何发文章，发官网docs:
<https://hexo.io/docs/writing.html>

