---
layout: post
category: blog
title: 从零在github-pages上部署个人博客
tagline: by Jiayuan 2015-7-22
tags: [blog,github-pages]
---

<!--more-->
1. 注册github账号，我们设账号为username
2. 在github上建立名为username.github.io的项目
3. github会自动为你在URL:username.github.io上部署页面
4. github依据jekyll的目录结构进行页面生成，其核心是三个部分
5. _config.yml，jekyll核心文件之一，内部参数相当于全局变量，可按照site.arg访问
6. _layout，复用页面结构，一般为default(nav导航，sidebar边栏，footer页脚等)、page(也基于default,包括404、about等页面)、post(文章页面，加入评论等)
7. _include，复用代码，如评论用代码、页面分析用代码、按catogory分类代码、按tag分类代码等
8. 放在根目录下的页面们，如index、404、about等等，里面的内容会放在layout中的content中
9. 这些都是github可以为你解析的，如果想本地调试，还需要构建本地环境
10. git环境，使用git for windows即可，现在方便多了，客户端会为你配置，当然有一些功能还是使用bash方便
11. jekyll环境，jekyll是基于ruby编写的，所以要先装ruby，安装时会为你自动配置path。jekyll是依赖于许多软件的，如果自己一一安装时很麻烦的，如果能打包到一起下载就方便多了。就像linux下的apt-get，yum等等。事实上，ruby-gem就是这样一个打包软件，而且ruby1.9.2后已经自带ruby-gem了，更加方便。只需用命令行cmd中输入gem install jekyll就可以在本地安装了，安装后不要忘记配置path。不过其默认库在国外的服务器上，所以基本连不上，可以使用ruby.taobao.org的库。如果想要与github的版本同步，可以直接gem install github-pages。
12. 本地运行。进入项目路径输入jekyll serve即可，目前是默认--watch模式，即监控修改，你在项目里该文件，它会立刻跟踪。在本地编写好网站和博客内容后，就可以通过github for windows push到github上了。
13. 现在的页面什么内容也没有，怎么办？可以使用github上的开源项目如jekyll-bootstrap，jekyll-now等作为框架，为你提供充足的引导
14. 现在的页面不漂亮，怎么办？可以使用github别人的作品，在jekyll theme项目里收录了很多，fork下来，就可以写博客了。
15. 从纯白版，到框架，到主题，是三种层次，对个人来说，是方便也是偷懒。
16. 域名是username.github.io，想换怎么办？购买独立域名！国内域名需要国家备案，所以推荐去国外买，godaddy就是一个提供域名购买的网站，而且支持支付宝，可以找一找优惠吗，一年的域名并不贵，我们设买的域名为user.com
17. 由于众所周知的原因，我们连接不上godaddy的DNS服务器，所以我们需要国内服务器提供DNS服务。这里推荐DNSpod，提供免费的域名解析服务。
18. DNS配置。首先是godaddy，要把域名服务下的dns服务器指定为DNSpod的服务器。
DNSpod方面，要把你的域名下建立A记录，指向github的服务器，可以在github网站上查询。如果有二级域名的话，如www等，建立CNAME记录，指向username.github.io。
github方面，需要在项目根目录下建立CNAME文件（注意大小写），内容只有一行，就是你的user.com。（其实其他二级域名也是可以的，只要注意更改相应dns的配置即可）
19. 值得一提的是，如果你配置了www二级域名和一级域名。CNAME中是一级域名的话，github会为你自动重定向到一级域名；如果CNAME中写的是www二级域名的话，github就会重定向到www二级域名。
20. 博客上还有其他可增添的内容。评论：可以使用第三方平台提供的服务，如多说，disqus等。分析：监控网页流量，google analytics代码嵌入。搜索：google custom search engine。
自定义404页面：在根目录下建立404文件即可。
 
