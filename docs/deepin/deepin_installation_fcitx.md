> 搜狗输入法存在内存占用过高的问题，参考[Deepin 彻底解决搜狗输入法内存占用过高问题](https://www.oubayun.com/deepin-che-di-jie-jue-sou-gou-shu-ru-fa-nei-cun-zhan-yong-guo-gao-wen-ti.html)，得以解决，原文已不见，现记录下，以备不时之需。

#### 卸载搜狗输入法

<div align="center"><img src="https://i.imgur.com/mEWoZr5.png"/></div>

清除sogou输入法剩余设置

```bash
cd ~/.config
sudo rm -rf SogouPY*
sudo rm -rf sogou*
rm -rf fcitx* #如果这里没有进行删除操作，后面处理就相对来说比较麻烦。
```

<h4 >安装 google 拼音</h4>

```bash
sudo apt-get install fcitx-googlepinyin
```

配置输入法：`im-config`

<div align="center"><img src="https://i.imgur.com/BC3x2tU.png"/></div>

设置输入法：`fcitx-config-gtk3`

<div align="center"><img src="https://i.imgur.com/1GONAgq.png"/></div>

正常情况重启笔记本生效，如存在无法显示输入法托盘问题，可通过下面的方法解决。

<h4 >无输入法托盘解决方法</h4>

根据这个部署安装和配置输入法以后，如果您在任务栏的托盘上看不到输入法的托盘，那您可能还需要做以下操作。
```bash
sudo apt-get install fcitx-frontend-gtk3 fcitx-ui-classic
```
这时候查看启动输入法会发现以下错误：
```bash
fcitx -d
liwenbin@liwenbin-PC:~$ (WARN-4033 fcitx-config.c:922) 配置项不合法:  行150 缺少’=’
```
但在查看输入法进程的时候是启动的
```bash
fcitx-autostart
Fcitx is running correctly.
ps -ef | grep fcitx
```
这时候结束对应的输入法进程
```bash
pidof fcitx|xargs kill
```
再删除对应的fcitx目录
```bash
cd ~/.config
rm -rf fcitx*
```
再启动对应输入法
```bash
fcitx -d     #启动输入法工具
```
这时候在托盘上我们就可以看到对应的输入法托盘了。

<div align="center"><img src="https://i.imgur.com/ShzrxTQ.png"/></div>

*没有了搜狗输入法的搅局，世界瞬间清静了。*

