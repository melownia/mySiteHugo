---
title: "Building Website With Hugo|用Hugo框架建博客网站"
subtitle: ""
date: 2020-10-01T23:06:53-04:00
draft: false
author: "Monica"
authorLink: ""
description: ""

tags: [blog]
categories: [tech doc]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: true
license: ""
---



Demo: https://swallowblack.github.io/

### 1. 在mac上安装Hugo框架

在Hugo官网下载想要的安装包：[Hugo extended version](https://github.com/gohugoio/hugo/releases) (recommended).



![Screen Shot 2020-10-02 at 20.06.37](https://tva1.sinaimg.cn/large/007S8ZIlly1gjbttzrvvbj31ew086763.jpg)



按照官方指南： [official hugo installation guide](https://gohugo.io/getting-started/installing/)  进行安装。

根据自己的需要安装在电脑的相应位置，我选择了安装在 ~/bin。安装完成后记得将hugo路径添加到自己电脑的环境中（我的在.zshrc中添加路径）。

<!--more-->

### 2. 下载Lovelt主题文件

按照 LoveIt [official guide](https://hugoloveit.com/zh-cn/theme-documentation-basics/#5-%E6%90%9C%E7%B4%A2) 下载主题文件到自己的站点目录相应位置。

### 3. 站点基本配置

按照前面的 LoveIt [official guide](https://hugoloveit.com/zh-cn/theme-documentation-basics/#5-%E6%90%9C%E7%B4%A2)完成基本配置。

#### 3.1 在本地测试

```shell
# create a new post
hugo new posts/first_post.md
# 在本地运行
hugo serve
# 或者：
# -D: buildDraft 显示标记为草稿的博文
# --disableFastRender 可实时预览。不用此参数似乎也可以。
# -e production 开启一些特性如评论系统等
hugo serve -D --disableFastRender -e production
```



#### 3.2 发布到github page

```shell
hugo
```

执行该命令，会生成一个 `public` 目录, 包含你网站的所有静态内容和资源. 现在可以将其部署在任何 Web 服务器上。以github为例：

为public文件夹关联你的github page repo

```shell
git init
git remote add upstream https://github.com/xxxx/xxxx.github.io.git
git add .
git commit -m "xxxx"
git push upstream master
```

几分钟后即可在https://xxxx.github.io/ 看到你部署好的网站。为了方便可写一脚本deploy.sh放在站点根目录下，以后每次执行此脚本即可。

```shell
#!/bin/sh

# If a command fails then the deploy stops
set -e

printf "\033[0;32mDeploying updates to GitHub...\033[0m\n"

# Build the project.
hugo  # if using a theme, replace with `hugo -t <YOURTHEME>`

# Go To Public folder
cd public

# Add changes to git.
git add .

# Commit changes.
msg="rebuilding site $(date)"
if [ -n "$*" ]; then
	msg="$*"
fi
git commit -m "$msg"

# Push source and build repos.
git push upstream master
```



#### 3.3 文章模板

```shell
cp themes/LoveIt/archetypes/default.md archetypes
```



#### 3.4 添加评论系统

我选择的Valine，评论时不需要注册。在[LeanCloud](https://leancloud.app/) （我选择的国际版）注册和创建app用以管理评论和阅读量统计。需要在app中新建Comment，Counter类，详细步骤google，有许多参考文章。然后需要在站点配置文件valine相关配置中填写你在LeanCloud的id和key。

![Screen Shot 2020-10-02 at 19.59.03](https://tva1.sinaimg.cn/large/007S8ZIlly1gjbtttbcb9j30qo0oijtz.jpg)



#### 3.5 如何添加站内搜索功能

此LoveIt版本自带搜索功能，非常方便，只需使用LoveIt主题的默认配置即可。主题提供了另外一种方式，没有试过，默认的方式目前用着还好。

### 4. 如何在menu bar添加Github和RSS链接

在站点的配置文件config.toml添加一下内容即可

```shell
[menu]
  [[menu.main]]
    identifier = "github"
    pre = "<i class=\"fab fa-github fa-fw\"></i>"
    post = ""
    name = ""
    url = "https://github.com/swallowblack"
    title = "GitHub"
    weight = 4
  [[menu.main]]
    identifier = "rss"
    pre = "<i class=\"fa fa-rss fa-fw\"></i>"
    post = ""
    name = ""
    url = "https://swallowblack.github.io/posts/index.xml"
    title = "RSS"
    weight = 5

```

### 5. 如何使用lightgallery

在文章的前置参数中**lightgallery**: 如果设为 `true`, 图片的引用采用[image shortcode](https://hugoloveit.com/theme-documentation-extended-shortcodes/#image)的形式， 文章中的图片在鼠标点击后将可以按照画廊形式呈现。


```Markdown
{?{}{< image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcqft8cedj30qo0hsdh6.jpg" caption="wheat" >}}

{?{}{< image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" caption="sunflower" >}}
```

{{< admonition tip "This is a tip" false >}}
此处需要用到{?}转义: {?{}?{?{}{?}} => {.
{{< /admonition>}}


{{< image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcqft8cedj30qo0hsdh6.jpg" caption="wheat" >}}

{{< image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" caption="sunflower" >}}


Linking Images with figure shortcode

```Markdown
{?{}{< figure src="https://i.loli.net/2020/06/27/k3puFt1SbBLzv9i.jpg" title="osprey" link="https://swallowblack.github.io/osprey-back/" width=50% >}}
```

{{< figure src="https://i.loli.net/2020/06/27/k3puFt1SbBLzv9i.jpg" title="osprey" link="https://swallowblack.github.io/osprey-back/" width=50% >}}

如果在站点配置中设置
```shell
[markup.goldmark.renderer]
      # 是否在文档中直接使用 HTML 标签
      unsafe = true
```
将可以使用raw html syntax.

```html
<div>
    {?{}{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
    {?{}{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
    {?{}{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
</div>
```
<div>
    {{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
    {{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
    {{<image src="https://tva1.sinaimg.cn/large/007S8ZIlly1gjcy2cy1asj30qo0hrgqo.jpg" width="200px" >}}
</div>


### 6. 如何设置文章的特色图片featured image

在文章的前置参数中添加：

```yaml
featuredImage: ""
featuredImagePreview: ""
```

- featuredImage: 文章的特色图片
- featuredImagePreview: 用于在主页预览的文章的特色图片




