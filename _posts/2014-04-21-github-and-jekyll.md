---
layout: layout
title: 黄金搭档：Jekyll 与 Github 搭建网站
category: 技术
---
<h2>{{page.title}}</h2>
![illustration]({{ site.url }}/assets/images/jekyll-github.jpg)

### 1) 简介

Github 是代码托管网站，用户可以用来一起协作开发。目前很多开源项目均放在Github 上， 如 jQuery, Twitter 等等。 Github 提供了一个 Github Pages 的功能，简单配置就可以在上面建立网站。

Jekyll是一个简单的静态网站生成器(请注意，是静态！)，能根据网页源码生成静态文件。Jekyll生成的站点，可以直接发布到github上面，这样我们就有了一个免费的（美好吧，哈哈），无限流量的网站。其它介绍请自行google 或百度。



----
[Github Pages 文档](https://pages.github.com/)||
[Jekyll官方文档](http://jekyllrb.com/)
****



### 2）为什么用 Jekyll ?

####优点:
1. 空间免费 (300MB)，github托管，稳定安全，不用跟空间商斗智斗勇（我选用的最主要原因）。
2. 无需自己搭建服务器。
3. 允许本地服务器调试，脱离网络写文章毫无压力。
4. 能绑定顶级域名（譬如鄙人的博客: [liusongx.com](liusongx.com)）。
5. 使用标记语言，比如Markdown，排版一级棒。



####缺点：
1. 使用Jekyll模板系统，仅适合企业小网站，博客，文档介绍等。
2. 尽管有诸多插件，动态程序的部分有相当局限。
3. 基于Git，需要基本的知识，不像Wordpress有强大的后台。


----
[jekyll入门教程](http://t.cn/zOaDFjy)||
[jekyll进阶](http://t.cn/zl7pZUJ)||
[markdown教程](http://t.cn/aOsWkg)|| 
[git教程](http://training.github.com/)
****

### 3) 入门

像厨子一样，下手之前，手里得有点准备的材料。你需要的只有：一个github帐号。

入门最好的教材，莫过于[GitHub Pages 的官方主页](https://pages.github.com/) ，操作下，会有一个直观简单的认识。阮一峰的文章[《搭建一个免费的，无限流量的Blog----github Pages和Jekyll入门》](http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html)是使用 GitHub 和 Jekyll 搭建独立博客非常好的入门文章，强烈建议先阅读并操作一遍。


### 4) 上手

学习完上述材料，你走到一个十字路口，不得不面临几个选择:

    A.完全自己定制博客
    B.找一份框架，修改后使用
    C.从GitHub上fork别人的博客代码，在其中添加自己的文章

由A至C，你搭建网站的时间呈雪崩一样递减。以耗时最少的选项C作路线说明： 搜一些 github 的博客，在其项目页， 点击右上角的Fork，就到你的Github 页面，删除posts 里的博文，然后准备博文。




### 5) 写博文

* 安装Git
  [教程见此](http://git-scm.com/book/en/Getting-Started-Installing-Git)
* 在Git 里克隆刚刚叉下的项目    $ git clone git@github:你的Github帐号/刚刚叉下的项目名.git
* 用编辑器 (sublime text 2 等等)尽情大胆的写博文
* 按以下顺序，把它推到你的github 上。
{% highlight cucumber %}
    $ git add 你的文件名(如 2014-02-12-life.html)
    $ git commit –m “随便写，自己好认识就行”
    $ git remote add origin git@github:你的Github帐号/刚刚Fork下的项目名.git
    $ git push remote master
{% endhighlight %}

### 6) 洗干手，观赏战果。


### 7) 其它选择：

不喜欢Jekyll, 你有很多选择：

* Wordpress
* Drupal
* Python-Django
* ......



----
####推荐阅读材料：
* [使用Github Pages建独立博客](http://beiyuu.com/github-pages/)
* [使用Jekyll在Github上搭建个人博客](http://skyinlayer.com/search.html?tag=jekyll)
* [使用 GitHub, Jekyll 打造自己的免费独立博客](http://blog.csdn.net/on_1y/article/details/19259435)

