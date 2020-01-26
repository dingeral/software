> gitbook 的配置文件讲解

如果你想对你的网站有更详细的个性化配置或使用插件，那么需要使用配置文件。 
 
配置文件写完后，需要重启服务或者重新打包才能应用配置。  

gitbook 的配置文件名是 book.json，首先在项目的根目录中创建 book.json 文件。  

## book.json 中一些主要参数说明
| 参数        | 说明                                                                      |
| ----------- | ------------------------------------------------------------------------- |
| title       | 标题                                                                      |
| author      | 作者                                                                      |
| description | 描述，对应 gitbook 网站的 description                                     |
| language    | 使用的语言，zh-hans 是简体中文，会对应到页面的 lang="zh-hans"       |
| plugins     | 使用的插件列表，所有的插件都在这里写出来，然后使用 gitbook install 来安装 |
| links       | 目前可以给侧导航栏添加链接信息                                            |
| styles      | 自定义页面样式，各种格式对应各自的 css 文件                                 |

### 配置默认主题

默认的主题可以通过配置来做一下效果。  
比如侧边栏菜单显示标题数字，可以在配置文件的 pluginsConfig 参数中写入如下字段：
```
{
    "pluginsConfig": {
        "theme-default": {
            "showLevel": true
        }
    }
}
```

## gitbook 的一些实用插件

### 插件安装、使用方法

1. 在 book.json 的 plugins 参数中添加插件名。  

2. 终端使用 gitbook install 来安装插件，或使用NPM命令来单独安装：

npm install gitbook-plugin-插件名。  

3. 重启服务或者重新打包就能看见效果。  

4. 如果使用 gitbook install 安装的很慢，建议使用 npm init 初始化一个 package.json 文件，然后每个包通过 npm 命令安装，以后就可以通过 npm install一键快速安装依赖包了。
  
***注意***：

1. 插件一定先要在 book.json 文件里面 plugins 中才能生效，如果只是安装了插件，而没配置的话是不会生效的。  

2. gitbook 命令安装慢，而且是全部插件都安装一遍，如果只安装一个插件的话建议使用 NPM 命令安装。

book.json 主要内容：

```
{
    "title": "我的一本书",
    "author" : "you",
    "description" : "我第一本书的描述，很好",
    "language" : "zh-hans",
    "root": ".",
    
    "plugins": [
        "-lunr",
        "-search",
        "search-pro",
        "back-to-top-button"
    ],
    "pluginsConfig": {
        "fontsettings": {
            "theme": "white",
            "family": "sans",
            "size":  2
        }
}
```

### 默认插件

GitBook 默认带有5个插件：

highlight

search

sharing

fontsettings

livereload

如果要去除自带的插件，可以在插件名称前面加 -：

```
"plugins": [
"-search"
]
```

### 常用的插件
| 插件               | 含义和默认值                                                                 |
| ------------------ | ---------------------------------------------------------------------------- |
| search-pro         | 高级搜索（支持中文）在使用此插件之前，需要将默认的 search 和 lunr 插件去掉。 |
| splitter           | 侧边栏宽度可调节                                                             |
| back-to-top-button | 回到顶部按钮                                                                 |
| edit-link          | 在线编辑文件                                                                 |
| favicon            | 修改网站的 favicon.ico                                                       |
| prism              | 代码块颜色插件                                                               |
| hide-element       | 隐藏元素                                                                     |
| theme-fexa         | 网站主题                                                                     |
| kaTex              | 支持数学公式                                                                 |
| mathjax            | 支持数学公式                                                                 |
| mermaid-gb3        | 支持渲染 Mermaid 图表                                                        |
| graph              | 使用 function-plot 绘制数学函数图                                            |
| Chart              | 绘制图形                                                                     |
| todo               | 待办事项                                                                     |
| klipse             | 嵌入类似IDE的功能                                                            |


## 参考

- [GitBook插件整理 - book.json配置](https://www.cnblogs.com/mingyue5826/p/10307051.html)
- [个人建站—Gitbook 教程](https://yidaofei.com/post/20180920-build-website-gitbook-guide/)
- [npm](https://www.npmjs.com/)