<p align="center"><a href="https://telegram.org/" target="_blank" rel="noopener noreferrer"><img width="90" src="https://cdn.jsdelivr.net/gh/dingeral/CDN/deepinbook/Telegram_logo.svg" alt="Telegram logo"></a></p>

<h2 align="center">Telegram</h2>

---

### 软件简介

Telegram 是一款基于云的移动和桌面消息应用程序，专注于安全性和速度。Telegram有加密聊天的功能，使用这种功能，聊天双方的内容完全保密，不会担心被监控或被第三方偷窥。

和微信群一样，Telegram上有很多“电报群”，内容五花八门，从科技、娱乐，到区块链、炒币，应有尽有。而且，很多电报群加入时不需要别人邀请，知道地址后可以自己直接加入。此外，电报群不像微信群那样有500人的人数限制，很多电报群有成千上万的人，非常热闹。

### 安装

> 命令行

```bash
sudo apt-get install telegram-desktop
```
> 软件包安装

官网： telegram https://telegram.org/

选择对应安装包

下载，解压到
```
/opt/telegram
```

制作起动器
```
[Desktop Entry]
Categories=Network;InstantMessaging;Qt;
Comment=Official desktop version of Telegram messaging app
Exec=/opt/telegram/telegram -- %f
Icon=telegram
MimeType=x-scheme-handler/tg;
Name=Telegram Desktop
StartupWMClass=TelegramDesktop
Terminal=false
Type=Application
Version=1.8.1
X-Deepin-Vendor=user-custom
```
文件名为： `Telegram.desktop`

放在： `/usr/share/applications` 下即可

### 上网

打开 Telegram 的设置，找到“连接类型”，点“默认（使用 TCP）”。

选择“通过 SOCKS5 代理”，服务器地址写 “127.0.0.1”，端口是你在 SS 里面设置的本地端口，一般为“1080”。

### 注册账号

打开 Telegram，你会看到一个让你输入电话号码来注册账号的界面，你需要选择国家和区号（中国大陆是+86），然后输入你的手机号码。接下来你会收到验证码，将验证码输入后，再输入一些个人信息，注册就完成了。

### 汉化

目前 Telegram 的官方软件还不支持中文，页面都是英文的。

方法：打开 Telegram，搜索 @zh_CN 进入频道之后，会看见下载安装说明，简单明了。

### 使用

这个不用多说。

推荐个收集群组的机器人：GroupHub,自称致力于收录 telegram 中文圈优质群组。

还有：[Telegram群组，频道，机器人 - 汇总分享](https://congcong0806.github.io/2018/04/24/Telegram/)

### 参考

- [技术讨论：教你怎么玩电报（Telegram），telegram入门教程](https://www.aiweinews.com/archives/19737.html)
