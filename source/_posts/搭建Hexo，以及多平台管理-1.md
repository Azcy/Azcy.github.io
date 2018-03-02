---
title: 搭建Hexo，以及多平台管理
date: 2018-01-17 17:26:45
tags: github
---
# 搭建Hexo，以及多平台管理

---

### 背景：
之前都是通过github的redme.md来编写自己的博客，后来在与朋友的聊天中得知了通过hexo可以搭建漂亮的博客，搭建过程中也遇到了许多小问题。

### 搭建过程
#### 1.创建安装git以及创建github远程仓库（忽略）
#### 2.安装nodejs
#### 3.配置hexo
##### 3.1下载安装hexo

    $ npm install -g hexo-cli
    
##### 3.2若接下来使用hexo命令，出现以下错误
    ERROR Deployer not found : github
则运行以下命令

    $ npm install hexo-deployer-git --save
    
##### 3.3创建文件夹 /blog，安装依赖包

    $ hexo init
##### 3.4安装依赖包
    $ npm install

##### 3.5提交以及本地测试
    $ hexo g //生成
$ hexo s //发布到本地
    $ hexo d   // 部署
或者
    
    hexo d -g #在部署前先生成

然后用浏览器访问http://localhost:4000/，此时，你应该看到了一个漂亮的博客了，当然这个博客只是在本地的，别人是看不到的，hexo3.0使用的默认主题是landscape。

#### 4.部署到github
##### 4.1在github创建Repository，格式如下：
    yourname.github.io

##### 4.2hexo的配置文件，\hexo\_config.yml
```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site	这下面的几项配置都很简单，你看我的博客就知道分别是什么意思
title: Chillax blog	#博客名
subtitle: Goals determine what you are going to be	#副标题
description: Goals determine what you are going to be #用于搜索，没有直观表现
author: huangjunhui	#作者
language: zh-CN	#语言
timezone: 	#时区，此处不填写，hexo会以你目前电脑的时区为默认值

# URL	暂不配置，使用默认值
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://opiece.me  #域名
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory		暂不配置，使用默认值
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing	文章布局等，使用默认值
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag	暂不配置，使用默认值
default_category: uncategorized
category_map:
tag_map:

# Date / Time format	时间格式，使用默认值
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination	
## Set per_page to 0 to disable pagination
per_page: 10	#每页显示的文章数，0表示不分页
pagination_dir: page

# Extensions	插件配置，暂时不配置
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
plugins:
- hexo-generator-feed
theme: light	#使用的主题，即：E:\myblog\themes文件夹下的主题文件夹名

feed:	#之后配置rss会用，使用如下配置即可
  type: atom
  path: atom.xml
  limit: 20  

# Deployment	用于部署到github，之前已经配置过
## Docs: http://hexo.io/docs/deployment.html

deploy: 
  type: git
  repository: http://github.com/huangjunhui/huangjunhui.github.io.git
  branch: master
```
部署上github的配置重中之中在于这里：

        deploy: 
          type: git
    repository: http://github.com/huangjunhui/huangjunhui.github.io.git
       branch: master
    

    
### 5、发表一篇文章
终端输入：
    
    // 新建一篇文章
    hexo new "文章标题"
    
我们可以在本地博客文件夹source->_post文件夹下看到我们新建的markdown文件。

## 6、更换电脑后如何管理hexo博客
### 6.1先从github上clone下博客的源文件
    $ git clone git@github.com:yourname/yourname.github.io.git

### 6.2在本地创个文件夹，获取hexo的源文件（若没有安装hexo，则看上边的安装教程 npm install -g hexo）
    $ hexo init
    

### 6.3将以下文件拷贝到从github上克隆下来的文件中
    _config.yml
     package.json
     scaffolds/
     source/
     themes/
     
### 6.4模块安装，执行命令：/克隆目录
     npm install
     npm install hexo-deployer-git --save
     npm install hexo-generator-feed --save
     npm install hexo-generator-sitemap --save

### 6.5部署，执行命令：
    hexo g
    hexo deploy





