# This is my note about streaming media!

熟悉下目前的环境，集群是怎么搭建的。然后在此基础上还要简介几个问题。

其中最重要的是一个点播集群的功能问题。Docker

linux: 鸟哥的Linux私房菜
docker: docs.docker.com/ 
srs: https://github.com/ossrs/srs/wiki/v2_CN_Home

如果linux够熟悉的话，先熟悉下docker是什么
然后装个VMWare虚拟机在本地上熟悉一下。
熟悉这个Get Started
 
接下来熟悉docker swarm  Run your app in production -> Configure containers -> Scale your app -> Swarm mode overview

目前先熟悉这两块，利用docker swarm搭建集群特别方便。你们有问题可以在群里随便问，了解了咱们再进行下一步

你们对云计算这方面感兴趣的话，做这个可以让你们对集群有更多的了解。docker这个是很火也很方便的容器技术，docker swarm是一个容器编排项目，因为是docker官方的，所以可以很方便地和docker进行集成，以前没有swarm的话估计要使用kubernetes，我也没用过，是一个挺麻烦的东西。

点播集群的技术，简单点的方法是寻找开源的解决方案，如果没有的话我的想法是使用对象存储和SRS的录制进行对接，这方面你们可以多探索下

我的经验是，碰到问题直接找官方文档，最管用，没有再找其他的。先找其他的，再去找官方文档往往绕了一大圈。

那你可以开始尝试自己用docker+SRS建一个集群。

你们可以用OBS调试自己搭建的集群。

不过那方面我也没搞过，你可以研究一下，看看SRS的服务器支不支持，或者用一些已有的工具包试试，

你可以先研究下 有没有现有的服务器 支持将多路视频拟合成一路视频的

也可以搜索一下 别人的解决方案 主要是会议系统用的
