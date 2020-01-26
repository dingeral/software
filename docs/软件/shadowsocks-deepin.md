
<p align="center"><a href="https://github.com/lolimay/shadowsocks-deepin" target="_blank" rel="noopener noreferrer"><img width="80" src="http://images.lolimay.cn/18-9-28/52492273.jpg" alt="Shadowsocks logo"></a></p>

<h2 align="center">Shadowsocks for Deepin</h2>

Shadowsocks-deepin是一款专门为deepin打造的小飞机，科学上网必备！

### 使用

启动软件，未启动代理时，小飞机显灰色，右击，第一个选项为`启动系统代理`，第二个选项是`系统代理模式`，分别是  `PAC` 模式和全局模式。在全局模式下，所有网站默认走代理。而 `PAC` 模式是只有被墙的才会走代理，推荐 `PAC` 模式，如果 `PAC` 模式无法访问一些网站，就换全局模式试试。

![Imgur](https://i.imgur.com/z4PYVZu.png)

第三个选项是`服务器`，这个需要`SS`服务器，可以手动编辑，也可导入配置文件、扫描二维码等，注意设置超时时间。

<a href="https://imgur.com/zZ6BAFZ"><img src="https://i.imgur.com/zZ6BAFZ.png?2" title="source: imgur.com" /></a>

### 配置 PAC 模式(可跳过)
安装 pip
```bash
sudo apt-get install python-pip python-dev build-essential 
sudo pip install --upgrade pip 
sudo pip install --upgrade virtualenv
```
安装 Genpac
```bash
sudo pip install genpac
```
建立一个合适的目录并进入，在其中生成 pac 文件

注意，在执行时需挂系统代理 sock5，否则会出现获取 gfwlist 失败的情况：
```bash
genpac --proxy="SOCKS5 127.0.0.1:1080" --gfwlist-proxy="SOCKS5 127.0.0.1:1080" -o autoproxy.pac --gfwlist-url="https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt"
```

### 下载

<p align="center"><a href="https://files.lolimay.cn/shadowsocks-deepin_1.2.2_amd64.deb"><img src="https://i.imgur.com/LX3PE8H.png"/></a></p>

### 项目地址

[github](https://github.com/lolimay/shadowsocks-deepin/tree/master)

###issues

> `http://file.lolimay.cn`域名过期了，能不能支持本地修改pac配置文件？

目前（1.22）可以先把`GUI-config.json`配置文件中的`pacUrl`修改为 
```
https://files.lolimay.cn/autoproxy.pac
或
https://raw.githubusercontent.com/dingeral/CDN/master/aotu_pac/autoproxy.pac
```

修改前先记得关闭软件,暂时不识别本地的PAC地址。

默认配置文件位置在：
```
/home/{username}/.config/pikachu/shadowsocks-deepin/gui-config.json
```