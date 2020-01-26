> 本文主要讲解在 github 网站上发布一个书籍文档

# 准备：

- 账号：github 有账号
- git：代码管理工具
- Markdown：gitbook 主要使用 Markdown 语法来编写书籍的
- gitbook 工具：在本地开发需要安装此插件
- nodejs 环境：gitbook 插件需要的运行环境
- 一款 Markdown 编辑器：方便本地开发，推荐 Typora 或 Atom

# 开始工作

## 1.账号
这个默认你有的。

## 2.git

> sudo apt-get install git

## 3.Markdown

自学即可。

## 4.gitbook 工具

安装 gitbook

> npm install gitbook -g


## 5.nodejs 环境

安装 node 与 npm

> sudo apt install nodejs-legacy  
> sudo apt install npm

安装管理 nodejs 本身工具，n 模块

> sudo npm install -g n

升级 node 到制定版本，后面接版本号（可选）

> sudo n latest //最新版本  
> sudo n stable //稳定版本  
> sudo n lts //长期支持版本

升级 npm 到最新版本（可选）

> sudo npm install npm@latest -g

## 6.基本使用

### 6.1 初始化

初始化一本书的命令是 gitbook init，

首先在终端创建一个项目目录，并进入这个目录：

> mkdir book_name  
> cd book_name

```
~ gitbook init

warn: no summary file in this book 
info: create README.md 
info: create SUMMARY.md 
info: initialization is finished
```

gitbook init 会在空项目中创建 README.md 和 SUMMARY.md 两个文件：  
README.md 文件是项目的介绍文件。  
SUMMARY.md 是 gitbook 书籍的目录。

### 6.2 本地启动服务编写书籍
终端打开项目目录，使用 gitbook serve 启动服务：

```
~ gitbook serve

Live reload server started on port: 35729
Press CTRL+C to quit ...

info: 7 plugins are installed 
info: loading plugin "livereload"... OK 
……
info: loading plugin "theme-default"... OK 
info: found 5 pages 
info: found 0 asset files 
info: >> generation finished with success in 2.1s ! 

Starting server ...
Serving book on http://localhost:4000
```

然后根据终端的提示，在浏览器中打开 http://localhost:4000 查看书籍

***注意***：gitbook serve 命令会在项目中生成一个 _book 的文件夹,此文件夹就是最终生成的项目。

### 6.3 项目部署到 GitHub Pages

这部分需要使用 git 和 github 网站，如果你不会，请自行在网上搜索文档查看。

由于 gitbook 生成的项目跟文档的源码是两个部分，所以可以把文档放到 master 分支上，部署的网站放到 gh-pages 分支。  
1、首先需要在 github上 创建公共一个仓库。  
2、在项目中创建一个 .gitignore 文件，内容如下：

```
# 忽略 gitbook 生成的项目目录
_book
```

然后终端打开项目，输入如下命令,来提交文档源码：
```
git init
git add .
git commit -m '初始化gitbook本地项目'
git remote add origin https://github.com/username/bookname.git 
git push -u origin master
```
上面命令执行结束后，就会把代码提交到 github 上的仓库。  
注意仓库地址要替换成你自己的链接。

为了部署方便，可以创建一个脚本文件 deploy.sh，内容如下：
```
#!/usr/bin/env sh

echo '开始执行命令'
# 生成静态文件
echo '执行命令：gitbook build .'
gitbook build .

# 进入生成的文件夹
echo "执行命令：cd ./_book\n"
cd ./_book

# 初始化一个仓库，仅仅是做了一个初始化的操作，项目里的文件还没有被跟踪
echo "执行命令：git init\n"
git init

# 保存所有的修改
echo "执行命令：git add -A"
git add -A

# 把修改的文件提交
echo "执行命令：commit -m '初始化gitbook本地项目'"
git commit -m '初始化gitbook本地项目'

# 如果发布到 https://<USERNAME>.github.io/<REPO>
echo "执行命令：git push -f https://github.com/your_name/book_name.git master:gh-pages"
git push -f https://github.com/yulilong/book.git master:gh-pages

# 返回到上一次的工作目录
echo "回到刚才工作目录"
cd -
```

注意脚本中仓库地址要替换成你自己的地址。

文件保存后，在终端执行如下命令开始把最终项推送到 gh-page 分支：

> bash deploy.sh

执行成功后，在 github 网站上的仓库里面点击 Settings -> GitHub Pages 选项中 -> Source 里面选择 gh-pages branch 然后点击 Save 按钮，然后在 GitHub Pages 下面就会看见一个网站，这个网站就是最终的网站。

## 7.添加域名

### 7.1 域名解析配置（github）

首先找到域名管理，选择域名解析功能,选择 A 记录就可以了。

![Imgur](https://i.imgur.com/C4jOTLJ.png)

（1）A 记录 类型 记录值填写 IP 值，两种选择：

> 你的 `github.io` 的 `IP` 值  
> 在官方提供的四个 `IP` 中选择， 如上图。

（2）CNAME 类型，请选好主机记录，按主机记录类型填写记录值。

推荐选择的 @ ，那么记录值就填写按各位 github 名填写 your_name.github.io 就好了。

### 7.2 github pages 方面的 CNAME 文件配置

（1）在 github 的 github pages 的仓库根目录里加上 CNAME 文件，里面写上个人域名即可。

（2）或者直接在 github.io 仓库的 Settings 的 GitHub Pages 项直接设置 Custom domain。

## 参考
- [gitbook 使用教程](https://segmentfault.com/a/1190000017960359#articleHeader8)
- [个人博客记 —— Github pages 绑定个人域名](https://segmentfault.com/a/1190000011203711)
- [在 deepin 中安装 node 与 npm](https://real-jacket.github.io/2018/08/16/%E5%9C%A8deepin%E4%B8%AD%E5%AE%89%E8%A3%85node%E4%B8%8Enpm/)