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