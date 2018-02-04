# 安装

## 要求

为了PyMdown扩展能工作，有一些先决条件。

| 名称                                       | 需要 | 细节 |
| ----------------------------------------- | ---- | - |
| [Python Markdown 2.6.0+][python-markdown] | 是   | 必须安装Python Markdown，因为它是使用的Markdown分析器。|
| [Pygments 2.0.1+ (optional)][pygments]    | 否   | 如果Pygments语法突出显示是必需的，则必须安装Pygments。这可以省略， 和代码块（如果使用CodeHilite扩展）将是格式化程序，用于JavaScript代码荧光笔。 |

## 安装

点子安装很简单：

```bash
pip install pymdown-extensions
```

如果你想手动安装它， 运行 `#!bash python setup.py build` 和 `#!bash python setup.py install`.  您应该能够在命名空间`pymdownx.<extension>`下访问Python Markdown中的扩展。

如果你想修改代码, 你可以通过安装它: `#!bash pip install --editable .`.  这种方法将允许您立即看到您的更改，无需重新安装。 如果你想在虚拟机上这样做，你可以。

--8<-- "links.md"
