---
layout: article
title: How to burn U-disk under Ubuntu,Ubuntu系统下如何刻录U盘
tags: Burn U-disk Ubuntu ISO
---

### 在Ubuntu下，有两种方式来刻录U盘：  

#### 1) UNetbootin  

[下载地址](https://unetbootin.github.io/)

#### 2) 命令行 dd  

- 首先，查看U盘挂载路径： 

{% highlight  ruby linenos%}
sudo fdisk -l
{% endhighlight %}

我的U盘是挂载在 /dev/sda   

- 然后，执行命名，比如我要将Downloads目录下的Windows.iso文件刻录到U盘里，输入以下命令：

{% highlight ruby linenos%}
 sudo dd if=/home/XXX/Downloads/Windows.iso of=/dev/sda
{% endhighlight %}

[dd命令详解](https://blog.csdn.net/qq_15505637/article/details/77053513)
