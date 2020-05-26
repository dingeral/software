**Deepin 系统安装软件的 N 种方法**
---

> 对于 Linux 系统，安装软件真不是像 Windows 下那么简单，  
> 但多动手，也没那么困难，看完你就会了！

#### 通过深度商店安装

> 这是最简单，也是对新手最友好的方式

启动深度商店，然后按照左侧的分类选择，或者在搜索框输入软件名称找到后直接点击安装。

#### 下载的安装包扩展名是`.run`

下载后点击右键 --->属性 --->勾选 **允许以程序执行**。

然后直接双击安装，后面的安装过程就和 windows 下的软件安装方法一样了。

也可在当前目录的命令行下执行：

```bash
sudo ./*.sh
```

`*` 代表对应文件名

#### 下载的安装包扩展名是`.deb`

双击软件，软件包管理器会检查依赖关系，如果没有问题，点击安装软件包。如果存在依赖问题就需要自己下载依赖软件，先安装依赖了。

如果安装包需要管理员权限，输入管理员的密码。

#### 下载的安装包扩展名是`.AppImage`

下载好直接打开选择运行就OK。

#### 下载的安装包扩展名是`tar.bz，tar.bz2，tar.gz`

这种软件安装文件下载后直接解压到自定的目录即可，我是放到 `/opt/` 目录下。

> 下面以安装 Firefox 举例

下载后右键解压到当前文件夹,如果你想移动到其他目录，直接剪切，然后找到目录，右键点击目录，以管理员权限允许，然后粘贴。

找到执行文件添加运行权限就可以运行了。

目前启动还是比较麻烦，那就创建一个快捷启动方式。

新建一个文本文件，输入以下代码，并保存为 `firefox.desktop`, 然后把这个文件放到 `/usr/share/applications` 目录下。

```
[Desktop Entry]
Categories=Application;
Comment=Firefox
Exec=/opt/firefox/firefox
GenericName=Firefox
[Icon=/opt/firefox/distribution/extensions/cehomepage@mozillaonline.com/chrome_ntab/skin/logo/firefox.ico
Name=Firefox
Terminal=false
Type=Application
Version=55.0
```

#### 通过终端输入命令安装

例如安装 C++ 的编译器 GCC 。

输入：

```bash
sudo apt-get install cmake g++
```

然后回车，输入密码，按照提示，输入 Y 或者 N 完成安装。

#### 下载源代码，自己编译后安装

这个比较复杂和耗时间，如非必要，不建议新手自己编译安装。

但是这种方法好处不少：  

1. 软件库提供的软件一般比较老，编译源码安装可以体验最新的软件；
2. 编译源码安装的软件执行效率高，和计算机匹配度最高，稳定性最好。一般服务器最好源码安装。

#### 参考

[Deepin 系统安装软件的方法总结](https://bbs.deepin.org/forum.php?mod=viewthread&tid=181002&extra=)
