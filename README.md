# mentohust_for_zqu

  这是一个针对肇庆学院制作的一个锐捷认证客户端的项目，里面实现了锐捷的v3（v4）算法的认证。
  这个工程的原项目是由hyrathb写的，原地址是https://github.com/hyrathb/mentohust
  我只是针对我学校的认证做了对应的修改。
  在此感谢hyrathb的贡献和ShanQincheng给我的启发
  交流群：215617688【肇庆学院mentohust交流群】

#### 修改思路
  其实没有什么修改思路，我是直接按照ShanQincheng所放出的方 http://www.codingstory.com.cn/mo-gai-mentohust-v4ban-ben-de-xin-de  进行对代码修改。
  但是不同的高校可能会有不同的修改方式，我觉得用linux版本认证并对齐抓包这样的成功率会提高很多（因为windows版本的锐捷的V4认证的C语言数组找不出来，好吧只是对我这菜鸡来说）
  对于我学校来说我学校有MAC地址检验，在上面的教程中还缺少了MAC地址的修改。
  v3(v4)对应的数组也是按照上面的教程所做的，有趣的是用WinHex编辑器会发现截取的位置其实就是C语言编译出来的程序部分，所以截取开头的部分会有CPP，末尾部分有return的字眼。


#### 原作者原话
  现在updateing实现了一个加载支持修改数据包内容的EAPOL认证客户端并将本工程的认证算法做成了插件，更加容易适配各个学校，建议大家尝试https://github.com/updateing/minieap

  完全没怎么看原来的代码，瞎改的。
  加入了V4支持。具体算法看checkV4.c

  所有hash都是从算法在rhash和ampheck借来魔改的……。



#### 编译
===============
在linux下安装相应的环境直接执行
sudo -i(输入密码）
./autogen.sh
./configure
make


#### 使用方法
  1、静态IP用户请事先设置好IP；
  2、打开终端，输入sudo mentohust，回车；
  3、［正确］输入相应信息，如果认证成功，跳到第8步；如果提示“不允许使用的客户端类型”，按Ctrl+C结束认证；
  4、打开终端，输入sudo mentohust -w -f'锐捷目录下任意文件路径'，回车；
  5、如果认证成功，跳到第8步；如果提示“客户端完整性被破坏”，按Ctrl+C结束认证；
  6、将锐捷安装目录下的SuConfig.dat重命名为其他名字；
  7、打开终端，输入sudo mentohust，回车；
  8、如果是动态IP且不是Linux，打开相应设置去更新IP。
  9、以后认证只需打开终端，输入sudo mentohust，回车。
  10、要修改某些参数请输入mentohust -h查看帮助信息并据此修改，例如修改密码sudo mentohust -pNewPassword -w，要临时修改则不加-w参数。

1. 如何退出:
  不以后台模式运行mentohust时，按Ctrl+C即可退出；后台运行时使用sudo mentohust -k退出认证。

2. 查看帮助信息请输入：mentohust -h
更详细的帮助信息请参考：http://wiki.ubuntu.org.cn/锐捷、赛尔认证MentoHUST

3. 修改参数请根据帮助信息操作，例如修改用户名和密码：sudo mentohust -uUsername -pPassword -w
指定某些参数仅对当次认证有效请根据帮助信息操作，例如临时修改用户名和密码：sudo mentohust -uUsername -pPassword

4. 如果提示缺少libpcap.so.0.x而在/usr/lib/目录下已存在一个libpcap.so.0.x.y，输入以下命令：
sudo ln -s libpcap.so.0.x.y /usr/lib/libpcap.so.0.x
否则请安装libpcap。

#### 权责声明
  1、本程序所有涉及锐捷赛尔认证的功能均是来自前辈公开代码及抓包分析。
  2、本程序于个人仅供学习，于他人仅供方便认证，不得使用本程序有意妨害锐捷赛尔认证机制及相关方利益。
  3、一切使用后果由用户自己承担。
  4、本程序不提供任何服务及保障，编写及维护纯属个人爱好，随时可能被终止。
  5、使用本程序者，即表示同意该声明。谢谢合作。

源码可在项目主页获取：http://mentohust.googlecode.com/
联系作者：在http://mentohust.googlecode.com/留言或Email：mentohust@ehust.co.cc
