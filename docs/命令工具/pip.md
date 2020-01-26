### Python pip

#### 介绍

pip 是 Python 包管理工具，该工具提供了对Python 包的查找、下载、安装、卸载的功能。

（英语：Python Package Index，简称PyPI）
#### 安装
目前如果你在 python.org 下载最新版本的安装包，则是已经自带了该工具。

Python 2.7.9+ 或 Python 3.4+ 以上版本都自带 pip 工具。

pip 官网：https://pypi.org/project/pip/

你可以通过以下命令来判断是否已安装：
```bash
pip -V
```

如果你还未安装，则可以使用以下方法来安装：
```bash
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   # 下载安装脚本
sudo python get-pip.py    # 运行安装脚本
```
**注意**：用哪个版本的 Python 运行安装脚本，pip 就被关联到哪个版本，如果是 Python3 则执行以下命令：
```bash
sudo python3 get-pip.py    # 运行安装脚本
```
一般情况 pip 对应的是 Python 2.7，pip3 对应的是 Python 3.x。

部分 Linux 发行版可直接用包管理器安装 pip，如 Debian 和 Ubuntu：
```bash
sudo apt-get install python-pip
```
#### pip 最常用命令

**显示版本和路径**
```bash
pip --version
或
pip -V
```
**获取帮助**
```bash
pip --help
```

**升级 pip**  
```bash
pip install -U pip
```

**安装包**
```bash
pip install SomePackage              # 最新版本
pip install SomePackage==1.0.4       # 指定版本
pip install 'SomePackage>=1.0.4'     # 最小版本
```

**升级包**
```bash
pip install --upgrade SomePackage
```
升级指定的包，通过使用==, >=, <=, >, < 来指定一个版本号。

**卸载包**
```bash
pip uninstall SomePackage
```

**搜索包**
```bash
pip search SomePackage
```
    
**显示安装包信息**
```bash
pip show SomePackage
```

**查看指定包的详细信息**
```bash
pip show -f SomePackage
```

**列出已安装的包**
```bash
pip list
```

**查看可升级的包**
```bash
pip list -o
```

#### pip 镜像源安装软件包
在用 pip install 安装时，是直接下载 pypi 上的软件，各种原因我们访问国外网站有时比较慢，可能在安装时会很慢，甚至提示超时，安装失败。

所以国内有公司和大学就镜像了 pypi ，把上面的软件包都镜像到国内，通过他们的镜像源安装就会很快。

比较典型的镜像源有：

豆瓣：http://pypi.douban.com/simple/

阿里云：http://mirrors.aliyun.com/pypi/simple/

清华：https://pypi.tuna.tsinghua.edu.cn/simple

比如使用清华大学镜像源安装就是：
```bash
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple 软件包名
```
但是镜像源没法实时做到更新 pypi上 的软件包，所以有些软件包的版本可能不是最新的。

#### 导出本地所有软件包名和版本号
如果你要在另一台电脑上部署一个相同的 Python 软件包环境，尤其是你在本地开发测试好后，要提交到生产环境去运行，要保证软件包的版本是一致的，上面讲了软件包版本不一致可能会导致程序出错。

这时就可以使用 freeze 命令导出本地的软件包名和版本号：

```bash
pip freeze > requirements.txt
```
上面命令会把软件包名和版本号导到 requirements.txt 文件里，然后把 requirements.txt 文件拷贝到另一台机器上，运行如下命令：
```bash
pip install -r requirements.txt
```
就会在另一台机器上完全安装跟本地一模一样的软件包环境。这比较方便开发和部署，以免本地的软件包和生产环境的不一致。

#### 参考
[Python pip 安装与使用](https://www.runoob.com/w3cnote/python-pip-install-usage.html)

[pip安装和使用入门指南](https://www.yuanrenxue.com/python/pip-usage.html)

[pip (软件包管理系统)][1]

[1]: https://zh.wikipedia.org/zh-hans/Pip_(%E8%BB%9F%E4%BB%B6%E5%8C%85%E7%AE%A1%E7%90%86%E7%B3%BB%E7%B5%B1)

