---
layout: post
title:  "Jekyll借助github搭建个人博客"
date:   2018-09-10 23:26:23 +0800
categories: jekyll update
--- 

借鉴处：
1. [官方Jekyll](https://jekyllrb.com/docs/troubleshooting/)  
2. [How to Set Up a Jekyll Development Site on Ubuntu 16.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-a-jekyll-development-site-on-ubuntu-16-04) 
3. [ufw使用](http://wiki.ubuntu.org.cn/UFW%E9%98%B2%E7%81%AB%E5%A2%99%E7%AE%80%E5%8D%95%E8%AE%BE%E7%BD%AE) 
4. [nano编辑器使用](https://www.vpser.net/manage/nano.html)
5. [bundle运行错误解决](https://kenshinsyrup.github.io/other/2017/02/09/Hello-World/)
6. [github page官网说明](https://pages.github.com/)

说下我的步骤：  
    
    1. 环境ubuntu18.04，sudo apt-get update
    2. 安装jekyll，sudo apt-get install ruby ruby-dev make build-essential  
    3. 编辑用户环境变量，vim .bashrc, 添加以下内容  
        # Ruby exports
        export GEM_HOME=$HOME/gems
        export PATH=$HOME/gems/bin:$PATH  
    4. 使环境变量生效， source ~/.bashrc
    5. 安装依赖管理，gem install jekyll bundler
    6. 开启防火墙，sudo ufw status
                 sudo ufw allow 4000
                 sudo ufw status  
    7. 创建静态网站，jekyll new mymyblog
    8. 运行静态网站，bundle exec jekyll serve
            出现Could not locate Gemfile or .bundle/ directory
            或Could not locate Gemfile都是指当前文件夹内无Gemfile  
            和Gemfile.lock文件，如果博客中使用了jekyll插件，则需要将插件写到文件  
            Gemfile中，如：  
            # If you have any plugins, put them here!  
            group :jekyll_plugins do  
            gem "jekyll-feed", "~> 0.6"
            gem "jekyll-paginate"
            end
    9. 登录github，创建仓库名为username.github.io，username为github用户名，然后将刚刚建立的静态网站上传到此仓库中，通过https://username.github.io即可访问。

