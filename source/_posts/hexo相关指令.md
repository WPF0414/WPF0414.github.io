---
title: hexo相关指令
toc: true
abbrlink: bafc0e00
date: 2019-11-18 20:18:25
comments: true
thumbnail: https://cdn.jsdelivr.net/gh/TRHX/ImageHosting/ITRHX-PIC/thumbnail/img.png
valine:
  placeholder: 你觉得这篇文章怎么样呢？
top: true
categories: 
- hexo
tags:
- hexo
---
写作时常用命令。
<!-- more -->
你可以执行下列命令来创建一篇新文章或者新的页面。

{% codeblock %}
$ hexo new [layout] <title>
{% endcodeblock %}

您可以在命令中指定文章的布局（layout），默认为 `post`，
可以通过修改`_config.yml`中的`default_layout`参数来指定默认布局。

## 布局（Layout）
Hexo 有三种默认布局：`post`、`page`和`draft`。在创建者三种不同类型的文件时，它们将会被保存到不同的路径；而您自定义的其他布局和`post`相同，都将储存到`source/_posts`文件夹。

| 布局 | 路径 |
|:--|:--|
| post | source/_posts |
| page | source |
| draft | source/_drafts |

{% blockquote %}
### 不要处理我的文章
如果你不想你的文章被处理，你可以将 Front-Matter 中的`layout:`设为`false`。
{% endblockquote %}
## 文件名称
Hexo 默认以标题做为文件名称，但您可编辑`new_post_name`参数来改变默认的文件名称，举例来说，设为`:year-:month-:day-:title.md`可让您更方便的通过日期来管理文章。

| 变量 | 描述 |
|:--|:--|
| :title | 标题（小写，空格将会被替换为短杠） |
| :year | 建立的年份，比如， 2015 |
| :month | 建立的月份（有前导零），比如， 04 |
| :i_month | 建立的月份（无前导零），比如， 4 |
| :day | 建立的日期（有前导零），比如， 07 |
| :i_day | 建立的日期（无前导零），比如， 7 |

## 草稿
刚刚提到了 Hexo 的一种特殊布局：`draft`，这种布局在建立时会被保存到`source/_drafts`文件夹，您可通过`publish`命令将草稿移动到`source/_posts`文件夹，该命令的使用方式与`new`十分类似，您也可在命令中指定`layout`来指定布局。

{% codeblock %}
$ hexo publish [layout] <title>
{% endcodeblock %}
草稿默认不会显示在页面中，您可在执行时加上`--draft`参数，或是把`render_drafts`参数设为`true`来预览草稿。
## 模版（Scaffold）
在新建文章时，Hexo 会根据`scaffolds`文件夹内相对应的文件来建立文件，例如：
{% codeblock %}
$ hexo new photo "My Gallery"
{% endcodeblock %}
在执行这行指令时，Hexo 会尝试在`scaffolds`文件夹中寻找`photo.md`，并根据其内容建立文章，以下是您可以在模版中使用的变量：

| 变量 |	描述 |
|:--|:--|
| layout | 布局 |
| title | 标题 |
| date | 文件建立日期 |

## 标签插件（Tag Plugins）
标签插件和 Front-matter 中的标签不同，它们是用于在文章中快速插入特定内容的插件。
### 引用块
在文章中插入引言，可包含作者、来源和标题。
**别号：**quote

```
{% blockquote [author[, source]] [link] [source_link_title] %}
content 
{% endblockquote %}
```
#### 样例
**‌没有提供参数，则只输出普通的 blockquote**
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
```
{% blockquote %}
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque hendrerit lacus ut purus iaculis feugiat. Sed nec tempor elit, quis aliquam neque. Curabitur sed diam eget dolor fermentum semper at eu lorem.
{% endblockquote %}
**‌引用书上的句子**
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
```
{% blockquote David Levithan, Wide Awake %}
Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
{% endblockquote %}
**引用 Twitter**
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}
```
{% blockquote @DevDocs https://twitter.com/devdocs/status/356095192085962752 %}
NEW: DevDocs now comes with syntax highlighting. http://devdocs.io
{% endblockquote %}
**引用网络上的文章**
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
```
{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}
### 代码块
在文章中插入代码。
**别名：**code
```
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}
```
#### 样例
**普通的代码块**
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
```
{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
**指定语言**
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
```
{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}
**附加说明**
```
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
```
{% codeblock Array.map %}
array.map(callback[, thisArg])
{% endcodeblock %}
**附加说明和网址**
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
```
{% codeblock _.compact http://underscorejs.org/#compact Underscore.js %}
_.compact([0, 1, false, 2, '', 3]);
=> [1, 2, 3]
{% endcodeblock %}
### 反引号代码块
另一种形式的代码块，不同的是它使用三个反引号来包裹。

\``` [language] [title] [url] [link text] code snippet ```
### Pull Quote
在文章中插入 Pull quote。
```
{% pullquote [class] %}
content
{% endpullquote %}
```
### jsFiddle
在文章中嵌入 jsFiddle。
```
{% jsfiddle shorttag [tabs] [skin] [width] [height] %}
```
### Gist
在文章中嵌入 Gist。
```
{% gist gist_id [filename] %}
```
### iframe
在文章中插入 iframe。
```
{% iframe url [width] [height] %}
```
### Image
在文章中插入指定大小的图片。
```
{% img [class names] /path/to/image [width] [height] "title text 'alt text'" %}
```
### Include Code
插入 `source/downloads/code`文件夹内的代码文件。`source/downloads/code`不是固定的，取决于你在配置文件中`code_dir`的配置。
```
{% include_code [title] [lang:language] [from:line] [to:line] path/to/file %}
```
#### 样例
**嵌入 test.js 文件全文**
```
{% include_code lang:javascript test.js %}
```
**只嵌入第 3 行**
```
{% include_code lang:javascript from:3 to:3 test.js %}
```
**嵌入第 5 行至第 8 行**
```
{% include_code lang:javascript from:5 to:8 test.js %}
```
**嵌入第 5 行至文件结束**
```
{% include_code lang:javascript from:5 test.js %}
```
**嵌入第 1 行至第 8 行**
```
{% include_code lang:javascript to:8 test.js %}
```
### Youtube
在文章中插入 Youtube 视频。
```
{% youtube video_id %}
```
### Vimeo
在文章中插入 Vimeo 视频。
```
{% vimeo video_id %}
```
### 引用文章
引用其他文章的链接。
```
{% post_path filename %}
{% post_link filename [title] [escape] %}
```
在使用此标签时可以忽略文章文件所在的路径或者文章的永久链接信息、如语言、日期。
例如，在文章中使用<code>&#123%post_link how-to-bake-a-cake %&#125</code>时，只需有一个名为`how-to-bake-a-cake.md`的文章文件即可。即使这个文件位于站点文件夹的`source/posts/2015-02-my-family-holiday`目录下、或者文章的永久链接是 2018/en/how-to-bake-a-cake，都没有影响。
默认链接文字是文章的标题，你也可以自定义要显示的文本。此时不应该使用 Markdown 语法 []()。
默认对文章的标题和自定义标题里的特殊字符进行转义。可以使用escape选项，禁止对特殊字符进行转义。
**链接使用文章的标题**
<code>&#123% post_link hexo-3-8-released %&#125</code>
[Hexo 3.8.0 Released](https://hexo.io/news/2018/10/19/hexo-3-8-released/ "Hexo 3.8.0 Released")
**链接使用自定义文字**
<code>&#123% post_link hexo-3-8-released '通往文章的链接' %&#125</code>
[通往文章的链接](https://hexo.io/news/2018/10/19/hexo-3-8-released/ "通往文章的链接")
**对标题的特殊字符进行转义**
```
{% post_link hexo-4-released 'How to use <b> tag in title' %}
```
**禁止对标题的特殊字符进行转义**
```
{% post_link hexo-4-released '<b>bold</b> custom title' false %}
```
[**bold** custom title](https://hexo.io/news/2019/10/14/hexo-4-released/ "<b>bold</b> custom title")
[](#引用资源 "引用资源")引用资源[](#引用资源)
引用文章的资源。
```
{% asset_path filename %}
{% asset_img filename [title] %}
{% asset_link filename [title] [escape] %}
```
[](#Raw "Raw")Raw[](#Raw)
如果您想在文章中插入 Swig 标签，可以尝试使用 Raw 标签，以免发生解析异常。
```
{% raw %}
content
{% endraw %}
```
[](#文章摘要和截断 "文章摘要和截断")文章摘要和截断[](#文章摘要和截断)
在文章中使用 `<!-- more -->`，那么 `<!-- more -->` 之前的文字将会被视为摘要。首页中将只出现这部分文字，同时这部分文字也会出现在正文之中。
例如：
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
<!-- more -->
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```
首页中将只会出现
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
```
正文中则会出现
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.

Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
```

注意，摘要可能会被 Front Matter 中的 `excerpt` 覆盖。
