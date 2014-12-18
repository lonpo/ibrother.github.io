---
layout: post
title: "jekyll 第二篇：首页显示文章全文"
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

看了默认模板的样子，艾玛，这是博客吗？也太简洁了吧。哈哈，默认(我装的时候jekyll是2.5.2版本)模板就是这个样子。
<!--more-->

让我们来看看blog目录下面有哪些东西

~~~
|- about.md
|- _config.yml
|
|- css-|
|      |- main.scss
|
|- feed.xml
|
|- _includes-|
|            |- footer.html
|            |- header.html
|            |- head.html
|
|- _layouts-|
|           |- default.html
|           |- page.html
|           |- post.html
|
|- _posts-|
|         |- 2014-12-15-welcome-to-jekyll.markdown
|
|- _sass-|
|        |- _base.scss
|        |- _layout.scss
|        |- _syntax-highlighting.scss
|
|- _site
```
~~~

`_config.yml`文件就是jekyll的主配置文件，jekyll相对于hexo的第二个难点就是配置文件太灵活，而且默认就给那么几个，太坑了有木有！。

`_includes`目录包含可重复使用的代码，只需要在其他文件中包含即可，比如在`_layouts/default.html`中加上一行`{% include head.html %}`,那个地方就被`_includes/head.html`填充进去。

`_layouts`中定义的是网页布局类型，比如默认定义了默认布局,页面布局，文章布局。布局文件可以有类似"继承"的特性，比如`page.html`和`post.html`在开头都加上了`layout: default`，这样表示他们本身是在默认布局的基础上更改的，通过include 和这种"继承"，可以大大减少重复代码量，也使整个结构更加清晰。

`_sass`里存放的是样式文件，最终生成`_site/css/main.css`

`_site`目录就是默认最终静态网页生成的目录，类似hexo中的`public`

ok，有了大致了解之后，我们再看看，默认模板还缺点啥？

哈哈，应该很容易发现的吧，默认的首页只显示了文章的时间和标题，这是不是更像归档的页面，我们一般都希望首页显示摘要或者文章的全文，so，just do it!

下面是`index.html`的部分代码

~~~ html
  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
      </li>
    {% endfor %}
  </ul>
~~~

略去无关的clss，这就是一个无需列表，通过liquid语句遍历所有的文章来生成这个无序列表,有日期，有文章标题链接，怎么加上内容呢？
我们在`</h2>`下面加上一行`<p>{{ post.content }}</p>`
此时`index.html`代码变成下面这样

~~~ html
---
layout: default
---

<div class="home">

  <h1 class="page-heading">Posts</h1>

  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
        </h2>
        <p>{{ post.content }}</p>
      </li>
    {% endfor %}
  </ul>

  <p class="rss-subscribe">subscribe <a href="{{ "/feed.xml" | prepend: site.baseurl }}">via RSS</a></p>

</div>
~~~

刷新一下，看内容是不是出来了，哦耶！

![][1]

[1]: http://7jpnam.com1.z0.glb.clouddn.com/jekyll_index1.png
