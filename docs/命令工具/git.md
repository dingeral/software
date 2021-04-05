### 基本操作

#### 安装

```bash
sudo apt-get install git
```

#### 配置用户名和电子邮件

```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
#### 初始化(在目标文件地址下)

```bash
git init
```

#### 创建SSH Key

```bash
#创建
ssh-keygen -t rsa -C "youremail@example.com"

#测试
ssh -T git@github.com
```

`id_rsa`是私钥，不能泄露出去，`id_rsa.pub`是公钥。

#### 网络代理

```bash
#配置
git config --global http.proxy 'socks5://127.0.0.1:1080'
git config --global https.proxy 'socks5://127.0.0.1:1080'
git config --global http.proxy 'http://127.0.0.1:1080'
git config --global https.proxy 'http://127.0.0.1:1080'

#查看代理
git config --global http.proxy

#删除代理
git config --global --unset http.proxy
git config --global --unset https.proxy
```

#### 保存密码

在使用Git 的时候，经常会遇到需要频繁输入密码的情况，每次 `git push` 和 `git pull` 都要求输入用户名和密码，如果提交频繁的话就十分不方便。

那么怎么解决Git保存用户名和密码呢？

1、进入Git 配置文件。

```bash
vim ~/.gitconfig
```

2、修改配置文件，添加下面内容。

```bash
[credential]
helper = store
```

然后使用的时候，输入一次用户名和密码之后，就不会出现再提交用户名和密码。


#### github 访问或下载慢

> 为何慢？

github 的 CDN 被某墙屏了。

> 解决办法

绕过 dns 解析，在本地直接绑定 host ，该方法也可加速其他因为 CDN 被屏蔽导致访问慢的网站。

> 原理

直接找出 github 域名所对应的 IP 地址，直接添加在本地 host 中。这样每次请求 gihub 时就无须在向 DNS 查询地址了。该方法也适用于其他被墙的地址，美中不足的是该方法必须为每个域名都添加上对应的 IP 地址。比较繁琐。

> 具体操作

手动 DNS 查找 IP 地址

访问 ipaddress 网站，查看网站域名对应的 IP 地址，输入网址则可查阅到对应的IP地址，这是一个查询域名映射关系的工具。

[https://www.ipaddress.com/](https://www.ipaddress.com/)

依次获取以下三个网址的 IP 

```
github.com

github.global.ssl.fastly.net

codeload.github.com
```

> 修改系统hosts

打开 hosts 文件并修改

```
sudo vim /etc/hosts
```

如图所示：

![Imgur](https://i.imgur.com/gGqY8ul.png?1)

> 重启网络服务

```
sudo /etc/init.d/networking restart
```
