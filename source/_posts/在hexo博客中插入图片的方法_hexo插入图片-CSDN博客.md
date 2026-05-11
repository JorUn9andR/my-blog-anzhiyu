---
title: "在hexo博客中插入图片的方法_hexo插入图片-CSDN博客"
source: "https://blog.csdn.net/2301_77285173/article/details/130189857"
author:
published:
created: 2026-05-07
description:
tags:
  - "clippings"
---
## 插入图片的方法

在完成了博客搭建、发布文章后，如果我们想在文章中插入图片，该怎么做呢？  
在使用网上的方法上传图片之后，我仍然遇到“图片无法显示”的问题，查阅官方文档并自己实践后，终于解决了，现将几种插入图片方法的步骤整理如下。

### 如果图片保存在本地

#### 方法一：全局资源文件夹

即，将所有文章的资源统一用一个全局资源文件夹管理。  
此方法的优点是比较 **简便** ，并且当多篇文章需要引用同一资源时，也比较方便。缺点是当文章很多时，各个文章的图片都在同一文件夹， **不便管理** 。

具体方法：  
在hexo文件夹下的source目录下，新建一个文件夹叫images(名字随意)，将要插入的图片放在该文件夹中。  
md文档内，使用`![图片](图片链接地址 "图片title")` 的格式，圆括号内的链接地址写(/images/name.jpeg)。  
这里的 / 指的是根目录，对于hexo，资源文件的根目录就是source。

例如，在md文档中写：`![图片](/images/20.jpeg "甘雨")`  
同时将“20.jpeg”这个图片文件放在hexo文件夹/source/images下，则图片可以上传到博客。

效果为：  
![甘雨](https://cf2imgbed.ccwu.cc/dav/img/b35fbbc13e7eb8df543f6ab255f0319b.jpeg)  
（图源网络，侵删)

![](https://cf2imgbed.ccwu.cc/dav/img/b35fbbc13e7eb8df543f6ab255f0319b.jpeg)

#### 方法二：文章资源文件夹

即，对于每篇文章，使用一个文件夹管理资源。  
此方法的优点是，当文章很多时， **便于结构化管理** 。缺点是，比方法一麻烦一点。

具体方法：  
2.1 修改hexo文件夹中的\_config.yml文件，如下：

```
post_asset_folder: true
marked:
  prependRoot: true
  postAsset: true
```

2.2 在终端cd到hexo文件夹， `hexo new [layout] <title>` 命令创建一篇新文章，此时会在hexo文件夹的source目录下，自动创建一个文件夹和.md文件。  
注：这句命令中的layout可暂时不写，使用默认的。title就是你的新文章的名字。如果文章名中有空格，务必将整个文章名用双引号引起来。如果文章名中没有空格，可以加双引号，也可以不加。  
例如，执行 `hexo new "如何发布文章到hexo博客上(含插入图片的方法)"` ，如下：

![hexo new命令](https://cf2imgbed.ccwu.cc/dav/img/322bc121b536468d07a1ec15e2beba1d.jpeg)  
会在source/\_post文件夹下生成一个"如何发布文章到hexo博客上(含插入图片的方法).md"文件。如下：

![source/_post文件夹](https://cf2imgbed.ccwu.cc/dav/img/54900e2cfaf95281e77a03ba60795fe8.png)

可以看到，同时还生成了一个同名的资源文件夹。  
2.3 我们可以将所有与该文章有关的资源（包括图片）放在这个关联文件夹中  
2.4 通过相对路径来引用图片资源。  
例如，将“1.jpeg”这个图片资源放在该文件夹中，并在.md文件中像这样引用图片：`![图片](1.jpeg)` ，这个方法在资源较多时方便管理。

### 如果图片为网络链接

添加图片，可以在md文档中，通过下面的方式引用图片，其中双引号内的图片title可省略。  
![请添加图片描述](https://cf2imgbed.ccwu.cc/dav/img/af2c2720268815c63a108a53ab65e940.png)

例如，输入：  

效果为：  

另附 **Typora编辑器中不显示图片** 的解决方案：  
安装下面的插件，可以使Typora等Markdown编辑器预览以及Hexo发布预览时，均能正常显示图片。  
`npm install hexo-asset-img --save`  
这样，如果你使用Typora编辑markdown文档，在typora内也可以显示图片了。