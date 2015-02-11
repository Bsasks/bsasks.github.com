---
layout: post
title: "Hello Octopress"
date: 2013-11-18 14:40
comments: true
categories:
---


![Alt text](/images/github_page_and-octopress.png)

<!--more-->

##准备

```
    Ruby：http://files.rubyforge.vm.bytemark.co.uk/rubyinstaller/rubyinstaller-1.9.3-p429.exe

    DevKit：http://cloud.github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe

    Python：http://www.python.org/ftp/python/2.7.5/python-2.7.5.msi

    Octopress：git://github.com/imathis/octopress.git  

    Git：http://msysgit.googlecode.com/files/Git-1.8.1.2-preview20130201.exe
```

##安装
     安装Git
     Windows下安装Git很简单，一路next就可以了。


##安装Ruby
Ruby的安装也是一路next就可以，不过记得勾选“Add Ruby executables to your PATH”，将Ruby的执行路径加入到环境变量中，如果忘记勾选，也可以手动设置。安装完后可以在命令提示符中输入ruby –version 来确认是否安装成功。修改环境变量，解决中文问题
```
   LANG=zh_CN.UTF-8
   LC_ALL=zh_CN.UTF-8
```

##安装DevKit

1. 解压到D:/DevKit，解压目录中没有有中文和空格；

2. 必须先安装Ruby，而且Ruby需要是RubyInstallser安装。

解压DevKit后，在命令行输入以下命令来进行安装：

   
```
     d:
     cd DevKit
     ruby dk.rb init
     ruby dk.rb install
```


##安装Octopress

首先在GitBash中输入如下命令将Octopress代码clone到本地，


```
     cd d:/GitProject
     git clone git://github.com/imathis/octopress.git octopress
```


然后需要安装Octopress的依赖项，安装依赖项需要用到Ruby的gem，使用下面的命令可以更换gem的更新源，使用国内的淘宝镜像速度相对快点。

```
     gem sources -a http://ruby.taobao.org/
     gem sources -r http://rubygems.org/
     gem sources -l
```    

修改Octopress目录下的Gemfile文件，将第一行的http://rubygems.org/ 修改为http://ruby.taobao.org/

在命令提示符中进入到Octopress目录，输入下面命令进行依赖项的安装


```
     gem install bundler
     bundle install
```


##安装Octopress的默认主题


```
   rake install
```

##本地进行预览。



```
     rake preview       #  这个时候在浏览器里输入 localhost:4000  就可以看到本地项目了
```



 



##发布文章


```
     rake new_post["title name"]
```
    
  注意，rake new_post['my first octopress blog']中的my first octopress blog并不是博客标题，而是和生成的文件名以及url地址有关，该名称不支持中文。
  博客标题可以在生成的markdown文件中修改。生成的markdown文件在octopress/source/_posts目录中,编辑 markdown文件。
  每次添加了博客的命令后，或者修改了内容都需要执行  rake  generate  重新生成

##将Octopress发布到Github

  登录到Github，创建一个名为username.github.com的repository，例如 xxx.github.com; 在命令提示符中进入到Octopress目录，输入下面命令：


```
     rake setup_github_pages
```    


按照提示输入新建的repository的地址，例如我的地址为：


```
     git@github.com:xxx/xxx.github.com.git
```


执行命令rake deploy 就可以将本地的内容发布到Github上。最后需要将Octopress的源文件推送到Github的Source分支上，执行下面命令即可;
    
    
```
     git add .
     git commit -m “your message”
     git push origin source
```    

[参考](http://www.cnblogs.com/oec2003/archive/2013/05/27/3100896.html)