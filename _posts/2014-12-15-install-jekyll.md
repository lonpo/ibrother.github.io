---
layout: post
title: "jekyll 第一篇：安装jekyll"
description: 
headline: 
modified: 2014-12-15
category: jekyll
tags: [blog, jekyll]
image: 
  feature: 
comments: true
mathjax: 
---

[静态博客][1]里，除了大家在目前在用的[hexo][2],还有一款很有名的静态博客引擎---[jekyll][3],相比较而言，hexo要方便很多很多，但是jekyll要更加贴近"汽车的发动机"，了解jekyll可以帮助了解这些模板引擎的工作原理，更让大家珍惜hexo的简单易用。
<!--more-->

# 安装过程

## 安装依赖

* [Ruby][4]

* [RubyGems][5]

* Linux,Unix,或者OS X

* [NodeJS][6]

Windows用户不哭哈，你们的教程在[这里][7]，可以负责任的说会遇到编码问题和文件监视功能缺失问题，这个是[解决方案][8]

Gentoo用户可以偷个懒`sudo emerge -av jekyll nodejs`一键完成

## 安装Jekyll

~~~ bash
$ gem install jekyll
~~~

# 创建博客

用下面的命令初始化一个目录作为博客目录，比如`blog`

~~~ bash
$ jekyll new blog
$ cd blog
$ jekyll serve
~~~

然后在浏览器中打开<http://127.0.0.1:4000/>，就可以看到默认的模板是这个样子，实在是。。。额，大道至简T\_T

![][9]

[1]: https://staticsitegenerators.net

[2]: http://hexo.io

[3]: http://jekyllrb.com

[4]: http://www.ruby-lang.org/en/downloads/

[5]: http://rubygems.org/pages/download

[6]: http://nodejs.org/

[7]: http://jekyll-windows.juthilo.com/

[8]: http://jekyllrb.com/docs/windows/#installation

[9]: http://7jpnam.com1.z0.glb.clouddn.com/jekyll_index.png
