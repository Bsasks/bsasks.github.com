---
layout: post
title: "Hello Github"
date: 2013-11-18 14:40
comments: true
categories:
---

##将Octopress发布到Github

<!--more-->
登录到Github，创建一个名为username.github.com的repository，例如 xxx.github.com；

在命令提示符中进入到Octopress目录，输入下面命令：
```
rake setup_github_pages
```

按照提示输入新建的repository的地址，例如我的地址为：
```
git@github.com:xxx/xxx.github.com.git
```
执行命令rake deploy 就可以将本地的内容发布到Github上。

最后需要将Octopress的源文件推送到Github的Source分支上，执行下面命令即可：

```
git add .
git commit -m “your message”
git push origin source
```