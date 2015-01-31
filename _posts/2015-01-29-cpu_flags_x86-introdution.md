---
layout: post
title: "CPU_FLAGS_X86-introdution"
description: Gentoo引入了新的变量来指示CPU优化
headline: 
modified: 2015-01-29
category: Gentoo
tags: [gentoo]
image: 
  feature: 
comments: true
mathjax: 
---

好不容易能蹭上网，第一时间`eix-sync`,噹噹噹，news來了。大致內容如下：

X86(amd64)架構指令集和其他特性從USE標記中移到了一個單獨的USE標記組，這個新變量名叫`CPU_FLAGS_X86`。
爲了對特定CPU優化，用戶需要更新`make.conf`(和`package.use`)文件。比如，如果你的USE標記裏是下面這樣的

`USE="mmx mmxext sse sse2 sse3"`

這些標記需要複製到：

`CPU_FLAGS_X86="mmx mmxext sse sse2 sse3"`

注意：x86和adm64架構系統使用相同的`CPU_FLAGS_X86`變量。

如果不確定，可以使用`equery`命令查詢USE標記的描述，`equery`命令由gentoolkit包提供：

{% highlight bash %}
$ equery u media-video/ffmpeg
{% endhighlight %}

大部分的標記名和`/proc/cpuinfo`裏的名字對應，少數標記有例外，比如sse3指令集在`/proc/cpuinfo`裏也叫`pni`

爲了幫助用戶啓用正確的USE標記，gentoo提供了一個使用`/proc/cpuinfo`自動生成的Python腳本，可以在`app-portage/cpuinfo2cpuflags`包找到它：

{% highlight bash %}
$ emerge -1v app-portage/cpuinfo2cpuflags
$ cpuinfo2cpuflags-x86
{% endhighlight %}

爲了保證安全遷移以及和擴展倉庫保持兼容性，建議保留原有的USE設置直到沒有包使用他們。
