> linux下代理一般是通过 http_proxy 和 https_proxy 这两个环境变量，但是很多软件并不使用这两个变量，导致流量无法走代理。在不使用 vpn 的前提下，linux 并没有转发所有流量的走全局代理。但是可以用 proxychains-ng 为程序指定走代理。

**proxychains-ng** 是 proxychains 的加强版。

主要有以下功能和不足：

- 支持 http/https/socks4/socks5
- 支持认证
- 远端 dns 查询
- 多种代理模式
- 不支持 udp/icmp 转发
- 少部分程序和在后台运行的可能无法代理

#### 安装 proxychains-ng
- 下载源码

```bash
git clone https://github.com/rofl0r/proxychains-ng
```

- 编译安装 (可能需要 `sudo`)

```bash
cd proxychains-ng
./configure --prefix=/usr --sysconfdir=/etc
make 
make install
make install-config
```

#### 配置

通过源代码编译安装的默认为 `/etc/proxychains.conf`

```bash 
sudo vim /etc/proxychains.conf
```
proxychains-ng 的配置非常简单，只需将代理加入 [ProxyList] 中即可
```
quiet_mode
dynamic_chain
chain_len = 1 #round_robin_chain和random_chain使用
proxy_dns
remote_dns_subnet 224
tcp_read_time_out 15000
tcp_connect_time_out 8000
localnet 127.0.0.0/255.0.0.0
localnet 10.0.0.0/255.0.0.0
localnet 172.16.0.0/255.240.0.0
localnet 192.168.0.0/255.255.0.0

[ProxyList]
socks5  127.0.0.1 1086
http    127.0.0.1 1087
```

proxychains-n g支持多种代理模式,默认是选择 strict_chain。

- dynamic_chain：动态模式,按照代理列表顺序自动选取可用代理
- strict_chain：严格模式,严格按照代理列表顺序使用代理，所有代理必须可用
- round_robin_chain：轮询模式，自动跳过不可用代理
- random_chain：随机模式,随机使用代理

#### proxychains-ng 使用

proxychains-ng用法非常简单，使用格式如下:
```bash
proxychains4 程序 参数
```
#### proxychains-ng 测试

```bash
proxychains4 curl ip.cn
```

#### proxychains-ng 优化
在 /.zshrc 或 /.bashrc 末尾加入如下行：
```bash
alias pc='proxychains4'
```

#### 参考

[通过ProxyChains-NG实现终端下任意应用代理](https://www.hi-linux.com/posts/48321.html)