# docsify 简明使用教程

> 总是忘记怎么用`docsify`，所以写了这个。

## docsify 是什么

`docsify`是一个动态生成文档网站的工具。不同于 `GitBook、Hexo` 的地方是它不会生成将 `.md` 转成 `.html `文件，所有转换工作都是在运行时进行。

## 快速开始

推荐安装 `docsify-cli` 工具，可以方便创建及本地预览文档网站。

```bash
npm i docsify-cli -g
```

## 初始化项目

如果想在项目的 `./docs` 目录里写文档，直接通过 `init` 初始化项目。

```bash
docsify init ./docs
```

## 开始写文档

初始化成功后，可以看到 `./docs` 目录下创建的几个文件

- `index.html` 入口文件
- `README.md` 会做为主页内容渲染
- `.nojekyll` 用于阻止 `GitHub Pages` 会忽略掉下划线开头的文件

## 本地预览网站

```shell
cd docs
docsify serve docs
```

## 部署到 GitHub Pages

对文件 `git` 初始化

```shell
#与 docs 同级
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/dingeral/仓库名.git
git push -u origin master
```

GitHub Pages 支持从三个地方读取文件

- docs/ 目录
- master 分支
- gh-pages 分支

推荐直接将文档放在 `docs/` 目录下，在设置页面开启 `GitHub Pages` 功能并选择 `master branch /docs folder` 选项。

![](https://docsify.js.org/_images/deploy-github-pages.png)

## 配置项

配置在 `window.$docsify` 里。

### repo

配置仓库地址或者 `username/repo` 的字符串，会在页面右上角渲染一个 `GitHub Corner` 挂件。

```html
window.$docsify = {
  repo: 'docsifyjs/docsify',
  // or
  repo: 'https://github.com/docsifyjs/docsify/',
};
```

### maxLevel

默认情况下会抓取文档中所有标题渲染成目录，可配置最大支持渲染的标题层级。

最大为 6。

```
window.$docsify = {
  maxLevel: 4,
};
```

### subMaxLevel

自定义侧边栏后默认不会再生成目录，你也可以通过设置生成目录的最大层级开启这个功能。

```
window.$docsify = {
  subMaxLevel: 2,
};
```

### loadSidebar

加载自定义侧边栏，参考多页文档。设置为 `true` 后会加载 `_sidebar.md` 文件，也可以自定义加载的文件名。

```
window.$docsify = {
  // 加载 _sidebar.md
  loadSidebar: true,

  // 加载 summary.md
  loadSidebar: 'summary.md',
};
```

### auto2top

切换页面后是否自动跳转到页面顶部。

```
window.$docsify = {
  auto2top: true,
};
```

### logo

在侧边栏中出现的网站图标，你可以使用`CSS`来更改大小。

```
window.$docsify = {
  logo: '/_media/icon.svg',
};
```

### name

文档标题，会显示在侧边栏顶部。

```
window.$docsify = {
  name: 'docsify',
};
```

### themeColor

替换主题色。利用 `CSS3` 支持变量的特性。

```
window.$docsify = {
  themeColor: '#3F51B5'
};
```

### autoHeader

同时设置 `loadSidebar` 和 `autoHeader` 后，可以根据 `_sidebar.md` 的内容自动为每个页面增加标题。

`autoHeader: true,`

### notFoundPage

在找不到指定页面时加载`_404.md`:

```
window.$docsify = {
  notFoundPage: true,
};
```

加载自定义`404`页面:

```
window.$docsify = {
  notFoundPage: 'my404.md',
};
```

## 插件

### 全文搜索 - Search

全文搜索插件会根据当前页面上的超链接获取文档内容，在 `localStorage` 内建立文档索引。默认过期时间为一天，当然我们可以自己指定需要缓存的文件列表或者配置过期时间。

```
<script>
  window.$docsify = {
    search: 'auto', // 默认值

    search : [
      '/',            // => /README.md
      '/guide',       // => /guide.md
      '/get-started', // => /get-started.md
      '/zh-cn/',      // => /zh-cn/README.md
    ],

    // 完整配置参数
    search: {
      maxAge: 86400000, // 过期时间，单位毫秒，默认一天
      paths: [], // or 'auto'
      placeholder: 'Type to search',

      // 支持本地化
      placeholder: {
        '/zh-cn/': '搜索',
        '/': 'Type to search'
      },

      noData: 'No Results!',

      // 支持本地化
      noData: {
        '/zh-cn/': '找不到结果',
        '/': 'No Results'
      },

      // 搜索标题的最大层级, 1 - 6
      depth: 2,
    }
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
```

### emoji

默认是提供 `emoji` 解析的，能将类似 `:100:` 解析成 ￼。但是它不是精准的，因为没有处理非 `emoji` 的字符串。如果你需要正确解析 `emoji` 字符串，你可以引入这个插件。

```html
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```

### 外链脚本 - External Script

如果文档里的 `script` 是内联脚本，可以直接执行；而如果是外链脚本（即 `js` 文件内容由 `src` 属性引入），则需要使用此插件。

`<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/external-script.min.js"></script>`

### 图片缩放 - Zoom image

`Medium's` 风格的图片缩放插件. 基于 `medium-zoom`。

`<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/zoom-image.min.js"></script>
`

忽略某张图片

`![](image.png ":no-zoom")`

### 复制到剪贴板

在所有的代码块上添加一个简单的`Click to copy`按钮来允许用户从你的文档中轻易地复制代码。

`<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>`

### Tabs

这个插件用来在 `Markdown` 中显示选项卡。

- [文档和示例](https://jhildenbiddle.github.io/docsify-tabs/#/)

### 代码高亮

内置的代码高亮工具是 `Prism`，默认支持 `CSS`、`JavaScript` 和 `HTML`。如果需要高亮其他语言，例如`PHP`，可以手动引入代码高亮插件。

其他的语言高亮插件可以查看[Prims 仓库](https://github.com/PrismJS/prism/tree/gh-pages/components)。

### 横幅

在顶部添加一个简单而可爱的横幅，以宣布一些内容。

[docsify-top-bannner-plugin](https://github.com/anikethsaha/docsify-plugin/tree/master/packages/docsify-top-banner-plugin)

### 数学公式

```
plugins     : [

//数学公式
//----------------------------------------------
    function (hook) {
    hook.doneEach(function () {
        // 每次路由切换时数据全部加载完成后调用，没有参数。
        // ---------------------------------------
        if (typeof MathJax !== 'undefined') {
        MathJax.Hub.Queue(["Typeset", MathJax.Hub])
        }
    })
    }
]


<script src="https://cdn.jsdelivr.net/npm/mathjax@2.7.5/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script type="text/x-mathjax-config">
MathJax.Hub.Config({
    extensions: ["tex2jax.js"],
    jax: ["input/TeX", "output/HTML-CSS"],
    tex2jax: {
        inlineMath: [ ['$','$'], ["\\(","\\)"] ],
        displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
        processEscapes: true
    },
    "HTML-CSS": { availableFonts: ["TeX"] }
});
</script>
```

### 目录可折叠

``` 
function(hook, vm) {
    hook.doneEach(function() {
    document.querySelectorAll(".sidebar-nav > ul > li").forEach(
        function(node, index, nodelist) {
        var span = document.createElement("span");
        span.innerHTML = node.firstChild.data;
        span.style.cursor = "pointer";
        span.onclick = function(event) {
            var ul = event.target.nextElementSibling;
            if (ul.style.display === "none") {
            ul.style.display = "block";
            } else {
            ul.style.display = "none";
            }
        };
        node.firstChild.replaceWith(span);
        node.lastChild.style.display = "none";
    });
    var active = document.querySelector(".sidebar-nav li.active");
    if (active) {
        active.parentElement.style.display = "block";
    }
    });
}
```

## 外观自定义

可以通过修改 CSS 文件，使外观更舒服。

css 源文件地址 https://cdn.jsdelivr.net/npm/docsify/themes/vue.css

修改完后，将`css`文件上传到`github`，获得网址，替换本地网址。

通用：https://cdn.jsdelivr.net/gh/dingeral/CDN/docsify/theme/vue.css

### 去除目录分支前的 `-`

将 621 行`content: '-';`，改为`content: '';`

### 将普通文字颜色加深

将 57 行`color: #34495e;`，改为`color: #333;`

### 目录文字颜色修改

将 595 行`color: #364149;`，改为`color: #333;`

将 601 行`color: #505d6b;`，改为`color: #333;`

### 字体大小

将 59 行`font-size: 15px;`，改为`font-size: 17px;`

## other

- [表格问题](https://github.com/docsifyjs/docsify/issues/794)