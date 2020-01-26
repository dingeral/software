### Sublime
#### 简介
Sublime Text是一个代码编辑器，它具有漂亮的用户界面和强大的功能，例如代码缩略图，Python的插件，代码段、语法高亮等。还可自定义快捷键绑定，菜单和工具栏等。

#### 安装
> 应用商店安装


打开应用商店 --> 编程开发 --> sublime3
![](https://cdn.jsdelivr.net/gh/dingeral/CDN/sublime3.png)

<br />

> 命令行安装

```bash
#安装GPG密钥
wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -
#确保apt已设置为使用https源
sudo apt-get install apt-transport-https
#安装稳定版
echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
#安装开发版
echo "deb https://download.sublimetext.com/ apt/dev/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
#更新一下
sudo apt-get update
#安装
sudo apt-get install sublime-text
```

<br />

> 安装包安装

[点击打开官网](https://www.sublimetext.com/3)

选择下载。

#### 无法输入中文
```bash
sudo apt update && sudo apt upgrade

git clone https://github.com/lyfeyaj/sublime-text-imfix.git

cd sublime-text-imfix && ./sublime-imfix
```
#### 关闭自动更新
转到**首选项** - > **设置** - **用户**并添加：
```bash
"update_check": false
```

#### 参考
[sublime text 3](https://fengwenhua.top/2018/11/15/sublime-text-3/)