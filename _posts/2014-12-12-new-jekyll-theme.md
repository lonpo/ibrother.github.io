---
layout: post
title: "博客換到jekyll了"
description: 
headline: 
modified: 2014-12-12
category: jekyll
tags: [jekyll]
image: 
  feature: 
comments: true
mathjax: 
---
貌似博主比較愛折騰，用hexo的時候就不老實，稀飯換主題。這下更是直接換到jekyll.也是到處找模板，直到我看到了這個主题，一見傾心...
<!--more-->

目前用的jekyll這個主題名叫做omega,[項目地址][1]，[demo][2]

我在作者的基礎上作了一些修改:

1. 修改首頁背景圖片和文章背景圖片爲絕對路徑,方便將大的圖片放在其他地方加快網頁加載.

2. 修改默認評論系統爲多說.

3. 添加post頁面導航

4. 使用`<!--more-->`截取文章摘要.

5. 增加頂部加載進(BI)度(GE)條.

6. 改用solarized-light代碼高亮樣式,提高(BI)(GE).

7. 增加表格樣式,媽媽再也不用擔心寫的表格難看了.

8. 調整字體,引用樣式等細節.

9. 在作者主題的基礎上抽象出了toc,只要在md中include即可(目前的實現比較dirty)

10. 加入百度sitemap

[項目地址][3],[demo][4]

[1]: https://github.com/hmfaysal/hmfaysal-omega-theme

[2]: http://hmfaysal.github.io/hmfaysal-omega-theme/

[3]: https://github.com/ibrother/jekyll-omega-theme

[4]: http://blog.ibrother.me/jekyll-omega-theme/
