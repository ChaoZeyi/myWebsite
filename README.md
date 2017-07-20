## 如何建立自己的个人网站

一直想有一个自己的个人网站，最近看paper看累了，趁着休息时间特别关注了一下，感觉也不是很麻烦，哈哈，下面给出步骤。

### 注册域名

首先你要考虑是要注册国内的域名还是国外的域名，国外域名普遍比较便宜，不过还是推荐国内，毕竟在我大天朝！

国内（万维）：https://wanwang.aliyun.com/domain/?spm=5176.8142029.388261.208.KeczTJ

国外：https://sg.godaddy.com/zh/

然后就可以选择自己喜欢的域名，像热门的.com .cn一般都是比较快，一年50-100左右，而且很多都是已注册，所以如果你是个人网站用，推荐.me .pub等，便宜、选择多，不过我的第一选择lucky.pub还是已经被注册了=_=

### 虚拟主机

虚拟主机选的是阿里云独享虚拟主机，5GB网页空间，1GB独享内存，500MB的数据库，对于我这种只用来写写博客的人来说是完全够的！

![1500535573(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500535573(1).jpg?raw=true)

之后还可以考虑用来跑代码！

### 备案

巨坑啊，买了一个.pub的域名，到备案的时候，才发现国内任何服务器都不支持该域名的备案![1500531848(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500531848(1).jpg?raw=true)

在阿里云官网论坛提问，说是正在争取，哇，简直是坑，然后很多人推荐说可以使用国外服务器，感觉是从一个小坑跳到了一个大坑！！！！哎，逼我换一个域名啊！

备案的过程还是蛮麻烦，需要填写很多资料，然后等待审核！

### 搭建WordPress

很良心的是，在等待审核的过程中，阿里云赠送了一个临时的已备案域名，可供我们调试网站程序。

![1500539331(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500539331(1).jpg?raw=true)

在电脑地址栏输入ftp://主机地址，按回车，需要输入ftp登录名与密码（可以在主机站点信息中找到），查看我们服务器所有的文件：

![1500540011(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500540011(1).jpg?raw=true)

首先查看“请先看我.txt”（可能是编码问题，上图显示乱码）这个文件，这里介绍了每一个文件夹的功能与作用。

![1500541524(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500541524(1).jpg?raw=true)

我们需要关注的有两个目录：

/htdocs：主文件夹，于是我们现在把WordPress解压在htdocs这个目录下，如下图：

![1500541667(1).jpg](https://github.com/ChaoZeyi/myWebsite/blob/master/pics/1500541667(1).jpg?raw=true)

/myfolder：可以放一些隐藏文件，不会在网页上显示

然后复制wp-config-sample.php文件，修改数据库信息，并重命名为wp-config.php



### FAQ

- 不同的域名解析状态也不一样，像我之前申请的.pub域名，便宜（9/年），注册完之后绑定主机，就可以直接解析成功，在网页中访问；但像我后来注册的域名.xin，那么贵（88/年），要等到实名认证之后，才可以进行解析！
- ​

