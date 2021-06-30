### Markdown简介

Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯（英语：John Gruber）。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML（或者HTML）文档。这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。  

John Gruber 在 2004 年创造了 Markdown 语言，在语法上有很大一部分是跟亚伦·斯沃茨（Aaron Swartz）共同合作的。这个语言的目的是希望大家使用“易于阅读、易于撰写的纯文字格式，并选择性的转换成有效的XHTML（或是HTML）”。 其中最重要的设计是可读性，也就是说这个语言应该要能直接在字面上的被阅读，而不用被一些格式化指令标记（像是RTF与HTML）。

​由于Markdown的轻量化、易读易写特性，并且对于图片，图表、数学式都有支持，目前许多网站都广泛使用 Markdown 来撰写帮助文档或是用于论坛上发表消息。例如：GitHub、reddit、Diaspora、Stack Exchange、OpenStreetMap 、SourceForge等。甚至Markdown能被使用来撰写电子书。(摘自[Markdown](https://zh.wikipedia.org/wiki/Markdown))

<br/>
### 标题的字体大小


一级标题就是：# h1

二级标题就是：## h2

三级标题就是：### h3

四级标题就是：#### h4

五级标题就是：##### h5

六级标题就是：###### h6

![](https://i.loli.net/2018/10/18/5bc7e9fda2fbe.png)

好了，总共只有六级，字体依次减小.观察一下，你就会发现规律：一级标题就是一个`#`、一个`空格`和内容；二级标题就是两个`#`、一个`空格`和内容;以此类推，别忘了只有六级哟！也可使用快捷键 Ctrl加上数字1～6，输入内容。
<br/>
### **列表**

#### 无序列表

- 这个小点（即无序列表）是`-` + `空格` 实现的（千万不要忘记空格）  
`-`也可以换成`+`、`*`


#### 有序列表

`数字` + `.` + `空格` + `内容`，如果想跳出列表需要回车，再回车

```markdown
1. 这是有序列表（一定注意`.`后面有一个空格）
  1. 这是嵌套列表，如果使用请注意顺序，先做有序列表，再使用嵌套列表
2. 有序列表
3. 有序列表
```
<br/>

### 标签形式

```markdown
 `用英文输入下的Esc键下面的那个键（一对）即可达到此效果，一般用来写单句代码。`
```
`用英文输入下的Esc键下面的那个键（一对）即可达到此效果，一般用来写单句代码。`

<br/>

### 超链接

关于超链接：英文输入下的中括号`[]`，里面填上你想写的话，然后在后面小括号`()`
输入链接地址就可以了。

例：`[百度](https://www.baidu.com/)`
[百度](https://www.baidu.com)

<br/>

### 引用
```markdown
> 这是一段引用，用`>` + 空格 （不要忘了空格）来开始
```
> 这是一段引用，用`>` + 空格 （不要忘了空格）来开始

<br/>

### 阅读全文设置

目标：在网站首页只显示每篇文章的部分内容，不要全部内容都展示出来。

方法一：对于hexo主题博客，修改主题设置_config.yml，找到这段代码：
```
Automatically Excerpt. Not recommend.
Please use <!-- more --> in the post to control excerpt accurately.
  auto_excerpt:
  enable: false
  length: 150		
```
把 enable 的 false 改成 true 就行了，然后 length 是设定文章预览的文本长度

方法二：在你写 md 文章的时候，可以在内容中加上 ` <!--more-->` ，这样首页和列表页展示的文章内容就是 `<!--more--> `之前的文字，而之后的就不会显示了(注意单独一行)。

<br/>

### 内容强调

```markdown
字体 **加粗** 显示
字体 *斜体* 显示
字体 ***加粗并斜体*** 显示
```

> 字体 **加粗** 显示
>
> 字体 *斜体* 显示
>
> 字体 ***加粗并斜体*** 显示

<br/>

### 删除线

```markdown
这样来 ~~删除一段文本~~
```

这样来 ~~删除一段文本~~

<br/>

### 表格

```markdown
 | 列1   | 列2  | 列3  |
 | ----- | ---- | ----|
 | 第1行 | 12   | 13   |
 | 第2行 | 22   | 23   |
 | 第3行 | 32   | 33   |
```
| 列1   | 列2  | 列3  |
| ----- | ---- | ----|
| 第1行 | 12   | 13   |
| 第2行 | 22   | 23   |
| 第3行 | 32   | 33   |
```markdown
|左对齐|右对齐|居中|
|:-------|--------:|:--:|
|Computer|5000元|1台|
|phone|1999元|1部|
```
|左对齐|右对齐|居中|
|:-------|--------:|:--:|
|Computer|5000元|1台|
|phone|1999元|1部|

<br/>

### 插入图片

#### 插入本地图片

格式：`![图片名](图片地址，绝对、相对地址都可以)`

> **缺点：不灵活不好分享，本地图片的路径更改或丢失都会造成markdown文件调不出图。**

#### 插入网络图片

只需要在基础语法的括号中填入图片的网络链接即可，现在已经有很多免费/收费图床和方便传图的小工具可选。我用的是[sm.ms](https://sm.ms/)

例子：
```
![小狗狗](https://i.loli.net/2018/10/17/5bc75c7757b8b.jpg)
```
![小狗狗](https://i.loli.net/2018/10/17/5bc75c7757b8b.jpg)

#### 自定义大小

```
<img width = '500' height ='320' src ="https://tse2-mm.cn.bing.net/th?id=OIP.rF3VYN1CRvtyWBPU0I7kyQDMEy&p=0&pid=1.1"/>
```

<img width = '500' height ='320' src ="https://i.loli.net/2018/10/17/5bc75c7757b8b.jpg"/>

#### 图片居左、中和右

在`align`后边填入`left`,`center`,`right`其中一个即可
例子：
```
<div align=center><img width = '500' height ='320' src ="https://i.loli.net/2018/10/17/5bc75c7757b8b.jpg"/></div>
```
<div align=center><img width = '500' height ='320' src= "https://i.loli.net/2018/10/17/5bc75c7757b8b.jpg"/></div>

<br/>

### 添加空行

使用`<br/>`即可

<br/>
### 换行
末尾两个空格，回车

<br/>
### 插入音乐

#### 插入单曲(对于hexo主题博客)

在网易云音乐里找生成外连接，复制过来就OK了，可惜的是很多都不能生成外联连接。如果想自动播放，可以把auto改成1。
```markdown
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=818820&auto=1&height=66"></iframe>
```

#### 插入歌单(对于hexo主题博客)

方法同上

```markdown
<iframe frameborder="no" border="1" marginwidth="0" marginheight="0" width=330 height=290 src="//music.163.com/outchain/player?type=0&id=2397184033&auto=0&height=430"></iframe>
```

每次修改id即可。

#### 使用aplayer播放器(对于hexo主题博客)

```
{% meting "60198" "netease" "playlist" "autoplay" "mutex:false" "listmaxheight:160px" "preload:none" "theme:#ad7a86"%}
```
#### HTML代码
```html
<audio src="https://blog.niostack.com/成都.mp3" controls="controls">
Your browser does not support the audio tag.
</audio>
```
<audio src="https://blog.niostack.com/成都.mp3" controls="controls">
Your browser does not support the audio tag.
</audio>

### 插入视频
```
<video src="https://raw.yiyoushuo.com/VIDEO/snqx0614~1.mp4" controls="controls">
Your browser does not support the video tag.
</video>
```
### 插入公式

#### 行内公式：使用 `$你的公式$`

使用 $你的公式$

#### 单行公式

```math
$$a{b^c} = (1 + a^b) ^{ -2ac^b}$$
```

$$ a{b^c} = (1 + a^b) ^{ -2ac^b} $$


<br/>

### 上标、下标

#### **上标**

```html
n<sup>2</sup>=n+1
```
n<sup>2</sup>=n+1

#### **下标**

```html
a=log<sub>2</sub>b
```
a=log<sub>2</sub>b

<br/>
### 空格

#### 1. 直接写

- 半方大的空白 `&ensp;` 或 `&#8194;`

- 全方大的空白 `&emsp;` 或 `&#8195;`

- 不断行的空白格 `&nbsp;` 或 `&#160;`

例：

```markdown
1&ensp;1&emsp;1&nbsp;1
```

1&ensp;1&emsp;1&nbsp;1

其中

- `&nbsp;` 表示半角空格（英文）表示全角空格（中文）
- `&emsp;`表示全角空格（中文）

#### 2.内嵌行公式空格

- 公式为：`$~~~~$`

<br/>

### 图文混排

使用 `<img>` 标签来贴图，然后指定 align 属性。

示例代码：
```
<img align="right" src="https://raw.githubusercontent.com/mzlogin/mzlogin.github.io/master/images/posts/markdown/demo.png"/>

这是一个示例图片。

图片显示在 N 段文字的右边。

N 与图片高度有关。

刷屏行。

刷屏行。

到这里应该不会受影响了，本行应该延伸到了图片的正下方，所以我要足够长才能确保不同的屏幕下都看到效果。
```

<img align="right" src="https://raw.githubusercontent.com/mzlogin/mzlogin.github.io/master/images/posts/markdown/demo.png"/>

这是一个示例图片。

图片显示在 N 段文字的右边。

N 与图片高度有关。

刷屏行。

刷屏行。

到这里应该不会受影响了，本行应该延伸到了图片的正下方，所以我要足够长才能确保不同的屏幕下都看到效果。



### 后记

至此Markdown的语法也写的差不多，当然以上是根据我的使用习惯写的，方便自己。

### 参考资料
- [Markdown语法说明](https://markdown.tw/)  
- [如何在markdown中打出上标、下标和一些特殊符号](https://www.jianshu.com/p/80ac23666a98)  
- [html特殊符号对照表](http://www.fhdq.net/ts/177.html)  
- [插入音乐_aplayer](https://github.com/MoePlayer/hexo-tag-aplayer/blob/master/docs/README-zh_cn.md)  
- [插入视频_dplayer](https://github.com/MoePlayer/hexo-tag-dplayer)  
- [Markdown 语言中空格的几种表示方法](https://blog.csdn.net/qq_34719188/article/details/84205243)  
- [Markdown学习笔记：如何画流程图](https://blog.csdn.net/zhaodedong/article/details/47671679)  
- [Markdown笔记：如何画流程图](https://segmentfault.com/a/1190000006247465#articleHeader0)
- [关于 Markdown 的一些奇技淫巧](https://mazhuang.org/2017/09/01/markdown-odd-skills/)

