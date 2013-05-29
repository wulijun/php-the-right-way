---
isChild: true
---

## 构建及部署你的应用 {#build_title}

如果你还在做手工的数据库模式修改或者在更新文件之前（也是手动的）手动进行测试工作，请三思而后行。
伴随每一个额外的手工任务你都需要部署一个你应用的新版本，发生潜在致命错误的机会增加了。
无论你是在处理一个简单的更新、一个复杂的构建过程甚至是使用一个持续集成的策略，
[自动构建](http://en.wikipedia.org/wiki/Build_automation) 都会成为你的朋友。

其中你可能想要自动完成的任务包括:

* 依赖管理
* 编译，压缩你的资源文件
* 进行测试
* 文档生成
* 封装打包
* 部署


### 自动构建工具

构建工具可以被描述为用于处理软件部署中的常用任务一系列的脚本。构建工具不是你软件的一部分，它在你的软件的外面起作用。

用很多的开源工具可以用来帮你完成自动构建的工作，有一些是用PHP写的有一些不是。
这不会影响你的使用，如果他们更适合特定任务的话，下面有一些例子：

[Phing](http://www.phing.info/) 是PHP世界里面最简单的工具可以让你上手使用自动部署。使用 Phing 你可以通过一个简单的
XML构建配置文件控制你的打包、部署或者测试过程。Phing (基于 [Apache Ant](http://ant.apache.org/)) 提供一系列丰富的
任务供你安装或升级一个Web应用，并且可以通过添加额外的自定义任务扩展其功能，通过PHP编写。

[Capistrano](https://github.com/capistrano/capistrano/wiki) 是一个可供 *中高级程序员* 以一种结构化、可复用的方式
在一台或多台远程机器上执行命令的系统。它被预先配置来部署 Ruby on Rails 应用，但人们成功地 **用它来部署PHP系统**
顺利使用 Capistrano 以来一些 Ruby and Rake 的工作知识.

Dave Gardner 的博客文章 [使用 Capistrano 进行PHP 部署](http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/) 
对于对Capistrano感兴趣的PHP开发者来说是一个好的开始点。

[Chef](http://www.opscode.com/chef/) 不只是一个部署框架，它是一个非常强大的基于 Ruby 的集成框架系统，它不仅
能部署你的应用还能构建你的整个服务器环境或者虚拟主机。

给 PHP 开发者的 Chef资源:

* [三部分博客系列：关于使用 Chef, Vagrant, 和 EC2 部署一个LAMP应用](http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/)
* [Chef 参考书： 安装配置 PHP 5.3 和 PEAR 包管理器](https://github.com/opscode-cookbooks/php)

扩展阅读:

* [使用 Apache Ant 自动化你的项目](http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/)
* [Maven](http://maven.apache.org/), 一个基于 Ant 的构建框架 和 [如何与 PHP 协同工作](http://www.php-maven.org/)

### 持续集成

> 持续集成是一种软件开发实践当一个团队里面的成员频繁地集成他们的工作时，通常每个人每天一次到多次集成。
> 许多团队发现这个方法可以显著减少集成问题并且允许一个团队开发拼合应用更加快捷。

*-- Martin Fowler*

在 PHP 中有很多不同方法实现持续集成，最近 [Travis CI](https://travis-ci.org/) 完成了一项伟大的任务使得持续集成变得现实
甚至在一些小项目里边。Travis CI 是一个托管的持续集成服务被用于开源社区。它被集成到 GitHub 并且对许多语言提供一等的支持
其中包括PHP。

扩展阅读:

* [使用 Jenkins 持续集成](http://jenkins-ci.org/)
* [使用 Teamcity 持续集成](http://www.jetbrains.com/teamcity/)
