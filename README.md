# 方圆小站Github仓库

---start---


---end---


## 2022年7月10日更新(Star破百纪念更新)

- 支持中文文件名, 由于WordPress本身的限制,文件名不要超过20个中文汉字(超过后会被默认WordPress配置截断, Star破200, 我会出一个突破20字符的方案), 比如: `2022-07-10-17-02-23-面试官应该给有潜力的面试者更多鼓励`(这算是17个中文字符)

![支持中文](https://cdn.fangyuanxiaozhan.com/assets/1657446551834PbkyDEWh.png)

## 用Github Actions写Markdown文章，自动更新到WordPress


- 写博客最舒服的格式是Markdown；

- 管理博客站最省心的方式是WordPress；

- 推广博客站最好的平台是Github；



这个项目可以让你用Markdown写博客，push更新到Github后，Github Actions自动将文章更新到WordPress，并将WordPres站的文章索引更新到Github仓库的README.md，供搜索引擎收录。



![image-20210119181051609](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123033557RhdS4nmK.png)



程序永久开源更新地址

[https://github.com/zhaoolee/WordPressXMLRPCTools](https://github.com/zhaoolee/WordPressXMLRPCTools)




### 如何实现WordPress登录授权？

WordPress默认开启了xmlrpc服务，xmlrpc是一套的统用的博客更新标准，允许用户以POST方式自动对文章内容进行增删改查。授权方式为 用户名 和 密码, 在WordPress中是后台登录的账户名和密码

我的WordPress网站为 [https://fangyuanxiaozhan.com](https://fangyuanxiaozhan.com) 

![image-20210119180338929](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123033711jFFFRE3D.png)

它的xmlrpc服务地址为  [https://fangyuanxiaozhan.com/xmlrpc.php](https://fangyuanxiaozhan.com/xmlrpc.php)

![image-20210119180403270](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123033808cFthmwwi.png)



### 使用Github Actions 有什么好处？

Github Actions 可以让我们无需安装开发环境，即可完成代码的运行。

![image-20210119180656968](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123033850KpH03KNE.png)

对于本项目而言，我可以用手机版Git App，或者Github网页完成新建文章, 然后push到仓库，Github Actions会自动帮我完成相关代码运行，代码可以帮我更新文章到WordPress网站，并生成新的文章目录索引，并自动给你更新到README.md, 供搜索引擎收录。



![image-20210119180529083](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123033950bTXn7Skr.png)


### 如何保护自己的WordPress账户密码？


Github 有一个secrets 功能，可以将用户名密码等关键信息保护起来，只有Github Actions可以读取到关键信息。

本项目需要设置三个secret



- WordPress登录用户名, 变量名为 USERNAME
- WordPress登录密码，变量名为 PASSWORD
- WordPress的xmlrpc.php，变量名为 XMLRPC_PHP







![image-20210119173133800](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/16111230341284PaHwCDm.png)



### 如何新建文章？

在`_post` 目录下新建 后缀为 `.md` 的markdown文件即可

![image-20210119181544158](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/16111230342738acPGWSM.png)



### 文章管理：如何为文章分类/加关键词标签？

在 `.md` 文件顶部填写以下初始化信息，即可完成标题（title），标签（tags），分类（categories）的设置，**其中title为必填项目**（这些关键词不是我定义的，我借用了著名静态博客构建工具 [hexo](https://github.com/hexojs/hexo) 的标准）








```
---
title: 我是标题
tags: 
- 我是0号标签关键词
- 我是1号标签关键词
- 我是2号标签关键词
categories:
- 我是1号分类
- 我是2号分类
---

```







## 标签(tags)和分类(categories)有什么区别？

标签(tags)是针对单篇文章的关键词，比如香蕉的标签有 **黄色**，**味甜** （标签是香蕉的属性）
分类(categories)是本篇文章的归属，比如香蕉的分类为 **水果**，**植物** 

![image-20210119182027684](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123034368EXM02d37.png)

###  如何设置固定链接？

对于博客而言，文章拥有一个固定的链接，是很重要的，我经过各种尝试，最终借鉴了 [简书](jianshu.com) 的文章url形式，域名后加 `/p/` , 再加英文文件名，只要不改变英文文件名，文章就有固定的链接，我在`_posts` 目录下新建一个 `2020-01-18-blog.md` 文件，同步后的文章url为 



[https://fangyuanxiaozhan.com/p/2020-01-18-blog/](https://fangyuanxiaozhan.com/p/2020-01-18-blog/)



文件名与网站url严格对应，既方便了修改，又可以在网站数据库出事故后，迅速从github仓库迅速恢复文章内容（容灾），连url都不会变。




![image-20210119171713841](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123034673aad52Amb.png)



## 如何使用？

完成以上配置后

每次在`_posts` 文件夹新增或更新文章后，运行

```
git pull && git add _posts && git commit -m "update" && git push
```

![image-20210119182503520](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123034888HbKthGTh.png)

即可！



![image-20210119182653436](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123036038n18wBCfT.png)



###  Github README.md显示效果,（新增的文章排在首位）



![image-20210119184015781](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/16111230361713668ZtFR.png)



### WordPress网站也同步发布了文章

![image-20210119182849720](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123036272XED7hTE0.png)

[https://fangyuanxiaozhan.com/p/2020-01-19-18-00-wordpressxmlrpctools/](https://fangyuanxiaozhan.com/p/2020-01-19-18-00-wordpressxmlrpctools/)



## 如何用手机完成博客更新操作？



![微信图片_20210119192838](https://raw.githubusercontent.com/zhaoolee/WordPressXMLRPCTools/master/README/1611123036503KhBJRrpj.jpeg)

用锤子便签，可以优雅舒适地写Markdown，手机App很好用，还有网页版可以用，有5GB的免费空间，能写到锤子倒闭。

如果遇到插入图片的问题，可以使用 免费图床图壳

[https://imgkr.com/#upload](https://imgkr.com/#upload)

Pocket Git 和 MT管理器可以配合完成Git 文件的新增更新和上传。





### 程序永久开源更新地址(求Star):



[https://github.com/zhaoolee/WordPressXMLRPCTools](https://github.com/zhaoolee/WordPressXMLRPCTools)



当我们把毕生所学，通过几十年如一日的博客更新，逐步开源到互联网上时，必将会造福更多志同道合的人。

