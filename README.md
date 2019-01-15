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

18.1.14
我们流媒体应用技术的研究开始于2014年，伴随远程课程、智慧教室、即时通讯的业务需求，从无到有逐渐成长。中间走了很多曲折的道路。经过团队一年来的非常有显著成效的努力，目前用在产品上的的是obs和ffmpeg.exe,基本满足了业务需要，但是具有延迟高、反应慢内存CPU占用高，定制性和集成度不高等问题。特别是近一年来很多关键技术逐渐突破，完全有可能基于ffmpeg SDK和web RTC等开源框架开发自有的系统，但需要大家一起努力，更上一层楼。

20190113版本，具有有推送三路Rtmp音视频至服务器，同时本地保存三路FLV文件，采集麦克音频，截屏，usb摄像头，IP摄像头视频，实时导播画面切换，及画中画，本地预览等功能。

链接：https://pan.baidu.com/s/1Z4pTYb9Ch1lcgm4QUq8SvQ 
提取码：ud8m 

目前的Demo版本涉及USB摄像头视频采集，截屏视频采集、视频动态拟合与切换及rtmp多路同时推送等功能，大家可以继续研究P2P推送、IP摄像头采集、更多视频拟合方式、本地文件保存等功能，以及降低资源优化性能等问题。基于该方案的会议系统已经开发成功。很快将以此为基础开发智慧教室PC4.0，欢迎一起参与。

链接：https://pan.baidu.com/s/1GQeBHjHe6poIW0cQlHJ0-A 
提取码：3ejw 

webrtc流媒体服务器采用的Kurento开源项目,官网地址:http://www.kurento.org/, IOS客户端支持这个流媒体服务器的开源项目有https://github.com/nubomediaTI/Kurento-iOS和https://github.com/nubomedia/Kurento-iOS，Android客户端支持这个流媒体的开源项目有https://github.com/nubomedia/nubo-test，web前端的js实现可参考kurento官方提供的demo

目前支持webrtc的流媒体服务器的测试环境已经搭建完成，流媒体服务器已经实现了信令，打洞服务器:stun:leisurely.org.cn:3478和turn:leisurely.org.cn:3478打洞服务器目前只有一个用户账号,username:xiazhenbo,password:123456,房间服务器地址:wss://leisurely.org.cn:8443/room

1.智慧教室会议系统@杨志鹏 @陈曦 @杨叙 @吕文玲 @任晓凡 @real__CuS ，研究rtmplib/ffmpegsdk集成替换obs技术.
2.web rtc@9527 @Focus @Andy @高丕基 @细心细心再细心 @初夏的风 研究跨越android ，IOS，web，PC的基于webrtc P2P方案，集成到新版的智慧教室，会议系统和即时通讯系统中。
3.rtmp服务器集群@黄坚强 @苏一桐 @大树 在保证流媒体服务集群安装部署维护的生产运行下，研究服务端的流拟合技术、动态分配docker资源等技术。

链接：https://pan.baidu.com/s/11FVL8gEgs_REWDiN67iSoQ 
提取码：a14j

会议系统新需求需要在流媒体服务器端将多路视频拟合一路视频。也需要跨平台支持p2p会议。另外需要用anyrtc或ffmpegsdk替换obs 进行Rtmp推流。请大家尽快分工研究。

初步考虑，智慧教室rtmp推拉流形式比较多样，延迟要求比较宽松，用Ffmpegsdk,会议系统rtmp推拉流形式单一，延迟要求高，用Srslibrtmp.两个系统都需要用web rtc用于辅导，远程课堂及讨论会。

通过现场安装与测试发现，开发智慧教室和会议系统Rtmp推拉流及WEBRTC P2P模块，势在必行，非常紧迫。

ffmpeg SDK 代码案例及webrtc原生代码（已编译，win10 最新版本及vs2017最新版）

链接：https://pan.baidu.com/s/11FVL8gEgs_REWDiN67iSoQ 
提取码：a14j

@初夏的风 @任晓凡 @real__CuS 你们三个主攻原生webrtc、ffmpegsdk客户端开发技术。@杨志鹏 @杨叙 和@吕文玲 之前开发的基于obs和ffmpeg.exe，vlc的rtmp推拉流客户端，下一步马上就要研发基于ffmpegsdk的智慧教室4.0.同时集成原生webrtc，@9527 目前正在研究基于android/IOS/web的web rtc客户端技术。都有非常多相互借鉴的技术。
