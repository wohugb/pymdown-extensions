# PyMdown扩展

## 用法

PyMdown扩展是Python Markdown扩展的集合。  请记住，PyMdown扩展的设计是为了与默认扩展配合使用，所以当与其他第三方扩展配对时，您的里程可能会有所不同。

所有的扩展名都在`pymdownx`下面。  假设我们想要指定MagicLink扩展的使用，我们会像Python一样将它包含在Python Markdown中:

```pycon3
>>> import markdown
>>> text = "A link https://google.com"
>>> html = markdown.markdown(text, ['pymdownx.magiclink'])
'<p>A link <a href="https://google.com">https://google.com</a></p>'
```

查看每个扩展的文档，了解更多关于如何配置和使用每个扩展。

!!! danger "提醒"
    请阅读[使用说明](usage_notes.md)以获取有关扩展兼容性的信息，以及使用这些扩展时需要注意的一般注意事项。

## 扩展

!!! summary "Arithmatex"
    [Arithmatex](extensions/arithmatex.md)是在Markdown转换过程中保留LaTeX数学方程($\frac{\sqrt x}{y^3}$) 的一个扩展，因此它们可以与[MathJax][mathjax]一起使用。

!!! summary "B64"
    [B64](extensions/b64.md) 将文档中的所有本地图像转换为base64编码并将其嵌入到文档中.

!!! summary "BetterEm"
    [BetterEm](extensions/betterem.md) 是与Python Markdown的默认不同的**重点**方法。  它的工作方式类似，但处理某些角落的情况不同

!!! summary "Caret"
    [Caret](extensions/caret.md) 是在`^`字符周围构建的扩展. 它增加了对插入超级^脚本^的支持 并添加一个简单的方法将^^文本^^放置在`#!html <ins>`标记中。

!!! summary "Critic"
    [Critic](extensions/critic.md) 增加了对[批评标记][critic-markup]的处理和支持.

!!! summary "Details"
    [Details](extensions/details.md) 用`#!html <details><summary>`标签创建可折叠的元素.

    ??? note "点击我!"
        谢谢

!!! summary "Emoji"
    [Emoji](extensions/emoji.md) 通过Markdown轻松添加表情符号 :smile:.

!!! summary "EscapeAll"
    [EscapeAll](extensions/escapeall.md) 允许逃离任何角色, 一些有额外的效果.  检查了解更多.

!!! summary "Extra"
    [Extra](extensions/extra.md) 就像Python Markdown的额外软件包一样，除了使用PyMdown扩展来代替类似的扩展.

!!! summary "ExtraRawHTML"
    [ExtraRawHTML](extensions/extrarawhtml.md) 暴露了Python Markdown在HTML块中解析降价的功能. 当你想要做的就是在HTML块中解析Markdown的时候，你不再需要包含所有的Extra.

!!! summary "Highlight"
    [Highlight](extensions/highlight.md) 允许您配置SuperFences和InlineHilite的语法高亮显示.  还通过语法高亮显示器传递标准Markdown缩进代码块.

!!! summary "InlineHilite"
    [InlineHilite](extensions/inlinehilite.md) highlights inline code: `#!py3 from module import function as func`.

!!! summary "Keys"
    [Keys](extensions/keys.md) 使按键输入到文档中就像按下一样简单 ++ctrl+alt+delete++.

!!! summary "MagicLink"
    [MagicLink](extensions/magiclink.md) 链接URL和电子邮件链接，而不必用Markdown语法包装它们. 此外，允许缩短资源库问题，拉取请求和提交链接。 你甚至可以使用轻松插入提及: @twitter:twitter.

!!! summary "Mark"
    [Mark](extensions/mark.md) 可以让你轻松==标记==单词.

!!! summary "PathConverter"
    [PathConverter](extensions/pathconverter.md) 将路径转换为绝对或相对于给定的基本路径.

!!! summary "ProgressBar"
    [ProgressBar](extensions/progressbar.md) 快速创建进度条

    [== 75%]{: .success}

!!! summary "SmartSymbols"
    [SmartSymbols](extensions/smartsymbols.md) 通过简单的ASCII表示插入常用的Unicode字符: `=/=` --> =/=.

!!! summary "Snippets"
    [Snippets](extensions/snippets.md) 在正在解析的当前Markdown文件中包含其他Markdown或HTML片段.

!!! summary "StripHTML"
    [StripHTML](extensions/striphtml.md) 可以去掉HTML注释和特定的标签属性.

!!! summary "SuperFences"
    [SuperFences](extensions/superfences.md)就像Python Markdown的栅栏，但更好。 在列表，告诫和其他语法下嵌套围栏。 还为UML等内容创建特殊的自定义栅栏。

    ```sequence
    Title: 这里是标题
    A->B: 正常线
    B-->C: 虚线
    C->>D: 打开箭头
    D-->>A: 虚线打开箭头
    ```

!!! summary "Tasklist"
    [Tasklist](extensions/tasklist.md) 允许用复选框插入列表.

    - [x] eggs
    - [x] bread
    - [ ] milk
 d
!!! summary "Tilde"
    [Tilde](extensions/tilde.md) Tilde是在`~`字符的语法上构建的。 它增加了对插入子~脚本~的支持，并增加了一个简单的方法将 ~~text~~ 放置在`＃!html <del>`标签中。

--8<--
refs.md

uml.md

mathjax.md
--8<--
