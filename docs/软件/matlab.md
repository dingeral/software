# Matlab 安装

## 下载

- [R2019b Windows](https://drive.google.com/file/d/1R4IKuQG7Db1KUDyKBuu-0dPLXJH4bV9w/view?usp=sharing)

- [R2019b Linux](https://drive.google.com/file/d/1sruBreiB-giFYCg9AbVYaleX8os7O-kM/view?usp=sharing)

- [R2019b MAC](https://drive.google.com/file/d/1OH7zZ-bEv83GqiDvQ16IFZwR5NFB85aD/view?usp=sharing)

## 安装

### 挂载镜像并开始运行 install 文件

```bash
cd  ~                                  # 切换到 home 目录
sudo mkdir  matlab                     # 创建一个文件夹，并命名为 matlab
sudo mkdir Linux                       # 创建一个文件夹，用来存放两个 ISO 文件（管理员打开才能移入）
sudo mount -t auto -o loop Linux/R2019b.iso matlab/              # 挂载
sudo matlab/install                    # 开始安装
```

当运行 install 文件后，会进入安装

### 选择“使用密钥安装”

![000301x8rlfx85l7klxobr.png](https://i.loli.net/2019/10/07/LSOw3CQM4BDImJo.png)

### 接受许可证协议

![000248i1d19j8rq03qqpr9.png](https://i.loli.net/2019/10/07/ZaNgGwR3tH61u2p.png)

### 输入密钥

![234813pfafa70vrjfjj7fa.png](https://i.loli.net/2019/10/07/Kbtp2mVP6BERk8c.png)

### 选择安装路径

![000252aoswxx44yxpsusbb.png](https://i.loli.net/2019/10/07/NOWMpzqr756XvmA.png)

### 选择需要安装的产品

![000253oozktd7f0f77k7g6.png](https://i.loli.net/2019/10/07/syO1oJ8GklMWPFZ.png)

### 开始安装

![000254onc3kealnvqvh7gv.png](https://i.loli.net/2019/10/07/co9TIfdEwu6m5nY.png)

### 安装完成

Next -> Finish

### 取消挂载

```bash
sudo umount matlab/
```

### 激活 Matlab

1.将 ~/Crack/bin/ 中的文件复制到 ~/MATLAB/R2019b/bin 中

2.以 root 权限运行 matlab

```bash
sudo /usr/local/MATLAB/R2016b/bin/matlab
```

3.选择离线激活

![000258shvvcrhe07smvcme.png](https://i.loli.net/2019/10/07/B9vqOKAXgcrID17.png)

4.选择 Crack 下的 license_standalone.lic 文件  

5.激活成功！  

6.创建快捷启动方式

```bash
sudo atom /usr/share/applications/Matlab2016b.desktop
```

粘贴下面代码后点击保存

```bash
[Desktop Entry]
Categories=Development;Matlab;
Comment[zh_CN]=Matlab: The Language of Technical Computing
Comment=Matlab: The Language of Technical Computing
Exec=sh /usr/local/MATLAB/R2019b/bin/matlab -desktop
GenericName[zh_CN]=Matlab2019b
GenericName=Matlab2019b
Icon=/usr/local/MATLAB/R2019b/toolbox/sl3d/mainpage/matlab_logo.gif
Mimetype=
Name[zh_CN]=MATLAB
Name=MATLAB
Path=
StartupNotify=true
Terminal=false
Type=Application
```

![000300ejtgmcnddsjjsctz.png](https://i.loli.net/2019/10/07/k4u7WTdJbeaD8Pr.png)

重启系统后，就可以使用啦！！！

![000257xftwcgbr8pphct77.png](https://i.loli.net/2019/10/07/PhGbm3j6nzpqETe.png)

![000250ejjoopqq7jo0vn3b.png](https://i.loli.net/2019/10/07/fpJFVc7mOHsXNz8.png)

### 问题

#### opengl

```
com.jogamp.opengl.GLException: X11GLXDrawableFactory - Could not initialize shared resources for X11GraphicsDevice[type .x11, connection :0, unitID 0, handle 0x0, owner false, ResourceToolkitLock[obj 0x413b9df1, isOwner false, <30fe5aac, af2eb55>[count 0, qsz 0, owner <NULL>]]]
  at jogamp.opengl.x11.glx.X11GLXDrawableFactory$SharedResourceImplementation.createSharedResource(X11GLXDrawableFactory.java:326)
  at jogamp.opengl.SharedResourceRunner.run(SharedResourceRunner.java:297)
  at java.lang.Thread.run(Unknown Source)
Caused by: com.jogamp.opengl.GLException: glXGetConfig(0x1) failed: error code Unknown error code 6
  at jogamp.opengl.x11.glx.X11GLXGraphicsConfiguration.glXGetConfig(X11GLXGraphicsConfiguration.java:570)
  at jogamp.opengl.x11.glx.X11GLXGraphicsConfiguration.XVisualInfo2GLCapabilities(X11GLXGraphicsConfiguration.java:500)
  at jogamp.opengl.x11.glx.X11GLXGraphicsConfigurationFactory.chooseGraphicsConfigurationXVisual(X11GLXGraphicsConfigurationFactory.java:434)
  at jogamp.opengl.x11.glx.X11GLXGraphicsConfigurationFactory.chooseGraphicsConfigurationStatic(X11GLXGraphicsConfigurationFactory.java:240)
  at jogamp.opengl.x11.glx.X11GLXDrawableFactory.createMutableSurfaceImpl(X11GLXDrawableFactory.java:524)
  at jogamp.opengl.x11.glx.X11GLXDrawableFactory.createDummySurfaceImpl(X11GLXDrawableFactory.java:535)
  at jogamp.opengl.x11.glx.X11GLXDrawableFactory$SharedResourceImplementation.createSharedResource(X11GLXDrawableFactory.java:283)
 ... 2 more
```

**解决**

```bash
matlab -softwareopengl

opengl('save','software')
```

## 参考

[Deepin安装MATLAB 2016b](https://bbs.deepin.org/forum.php?mod=viewthread&tid=174620&highlight=matlab)

[做有意义的事，活出自己的价值](http://kmshareall.blogspot.com/2019/09/matlab-r2019b-matlab-r2019b-windows.html)

[Could not initialize shared resources for X11GraphicsDevice](https://ww2.mathworks.cn/matlabcentral/answers/342906-could-not-initialize-shared-resources-for-x11graphicsdevice)

[解决MATLAB在linux下无法使用hardware openGL的问题](https://www.jarviswang.me/?p=467)

## 在线安装

### 下载安装文件

matlab_R2019b_glnxa64.zip为Linux平台

matlab_R2019b_maci64.dmg.zip为MacOS平台

matlab_R2019b_win64.exe为Windows平台。

### 运行下载的程序

Windows可能会弹出UAC允许即可；MacOS会提示输入账户密码，直接输入登录桌面的密码即可

![c640751c93936d2422c68615220ad0f89ec22a.png](https://i.loli.net/2020/04/06/3GcrQkVgfD2PiuR.png)

### 在接下来的选择安装方法中，选择使用MathWorks登录，点击下一步

![9287814349a76ff10530ea3a402434edec56ba.png](https://i.loli.net/2020/04/06/Cp3JQHdL9koa5Gq.png)

### 在弹出的许可协议中，选择是并点击下一步

![9a90d38e99a0ba6a3977622eac75be1df608b3.png](https://i.loli.net/2020/04/06/8DKMiYwRg9dbhTk.png)

### 在接下来的登录窗口中，登录MathWorks账号

账号：s1ugqg978@xkx.me

密码：Mat1ab@12

![fjhfgj](https://img.vim-cn.com/21/5633a5285f7e1ed915037169deb94186834298.png)

### 在许可证选择中，选择编号为 6990316 的许可证后点击下一步

![image.png](https://i.loli.net/2020/04/06/19anPy6KUiZqefI.png)

### 在文件夹选择中，一般保持默认即可，直接点击下一步

![image.png](https://i.loli.net/2020/04/06/wgzp7JoTNxMAvl2.png)

### 在产品选择中，全选并点击下一步

![image.png](https://i.loli.net/2020/04/06/1NvMI6zE7cHi25j.png)

### 接下来稍等片刻即可安装完毕

![image.png](https://i.loli.net/2020/04/06/S5edKLUvguYtTib.png)

### 激活

Crack 文件夹内有3个压缩包，分别对应着不同的系统平台，根据自己的系统选择合适的文件

在接下来的窗口中，点击下一步后关闭窗口

![image.png](https://i.loli.net/2020/04/06/hXxM7ZI5p3ryzSO.png)

复制破解文件，不同系统下复制的路径不相同

MacOS: 右击MATLAB_R2019b.app，显示包内容，然后将Crack文件夹内的 libmwlmgrimpl.dylib替换/bin/maci64/matlab_startup_plugins/lmgrimpl/libmwlmgrimpl.dylib

![image.png](https://i.loli.net/2020/04/06/fBYmTUloGPcM7ag.png)

Windows: 复制R2019b下的bin文件夹直接与安装目录根目录下的文件夹合并并替换相关文件即可

​手动替换请将libmwlmgrimpl.dll将/bin/win64/matlab_startup_plugins/lmgrimpl/libmwlmgrimpl.dll

​找不到安装路径，可以右击桌面的快捷方式，点击属性后点击打开文件所在位置就能看到

![image.png](https://i.loli.net/2020/04/06/xdi1coBHtkRq8Dv.png)

![image.png](https://i.loli.net/2020/04/06/l4w3PbyJ1K7TqAC.png)

再打开MATLAB，在弹出的激活窗口里面选择在不使用Internet的情况下手动激活后点击下一步

![image.png](https://i.loli.net/2020/04/06/mtbaI1LydA6OQZW.png)

在离线激活中，点击浏览，选择Crack文件夹下的license.lic或license_standalone.lic

![image.png](https://i.loli.net/2020/04/06/lGEq56fQSX94NF1.png)

点击下一步，即可激活完成

![image.png](https://i.loli.net/2020/04/06/rAQlHapWY6JBhVX.png)

### Q&A

1. 需不需要联网

需要，因为是在线安装。激活的时候也可以不断网
2. 安装完成之后，启动软件出现License Manager Error怎么办

一般情况下，这个报错是因为你没有替换dll文件或者过早的替换文件造成的，请返回上文中激活第二步仔仔细细阅读一下，再次重新覆盖一下dll文件，记住，一定要替换到正确的目录

如果正确替换了文件还是报错的话，有可能是你电脑内安装的MATLAB比较“混乱”。比如两个或两个以上版本的MATLAB还在同一个文件夹内、因为各种各样的原因导致安装过程中断等等等等。这里建议直接将你电脑上安装的所有版本全部卸载。然后使用一种方法重新安装即可。

![image.png](https://i.loli.net/2020/04/06/hDE29dQ3xBX6ALz.png)
![image.png](https://i.loli.net/2020/04/06/cwgsolx1M32VfpT.png)
