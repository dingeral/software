<h2 align="center">ssf2skin</h2>

`ssf2skin`是能将搜狗拼音皮肤转换为 `fcitx` 皮肤的小工具。

![Imgur](https://i.imgur.com/feM3tMY.png?2)

### 使用

> 转换皮肤

```
./ssf2skin -i input.ssf -o output_dir
```
`input.ssf` - 你要转换的搜狗皮肤，去官网看看你喜欢的，下载下来吧。
<br><br>
[搜狗皮肤官网](https://pinyin.sogou.com/skins/)

`output_dir` - 目标文件夹，即放置生成文件的地方，也可省去，会自动在当前文件中创建一个文件夹。
```
./ssf2skin -i input.ssf
```
比较偷懒的方法，也很实用，记得把文件名改为皮肤名。

> 放在正确的地方

将生成的文件夹移动到 `/usr/share/fcitx/skin` 或 `/home/用户名/.config/fcitx/skin`

> 切换皮肤，慢慢享受


### 注意

不是所有搜狗皮肤都能完美转化，不支持动图等。

### 下载

<p align="left"><a href="https://pan.baidu.com/s/1gQuSudI9uLML1Uqvy6Od2A"><img src="https://i.imgur.com/LX3PE8H.png"/></a></p>

### 官方地址

[**ssf2skin**](https://github.com/VOID001/ssf2fcitx)