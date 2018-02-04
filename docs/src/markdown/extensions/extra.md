# Extra

## 概观

Python Markdown有一个额外的扩展，提供类似于PHP Markdown Extra的功能。
PyMdown扩展旨在提供不仅新功能，而且改善Python Markdown现有功能集中的行为。
其中一些事情可能不一致。

Python Markdown的`smartstrong`和`fenced_code`不兼容PyMdown扩展的`betterem`和`superfences`。
,`smartstong`不应该与`betterem`同时加载，`superfences`不应该与`fenced_code`同时加载

因此，使用Python Markdown的`extra`和PyMdown Extensions `superfences`和`betterem`是不可能的,为了减少这个问题，PyMdown扩展提供了自己的`extra`实现。

PyMdown扩展`extra`就像Python Markdown的额外功能，除了`smartstrong`被`betterem`替代，`fenced_code`被`superfences`替代。
所有其他功能和扩展应该是相同的，因为我们使用相同的。

这个扩展是一个方便的扩展，它目前不提供其他附加功能。
But remember **don't use `pymdownx.extra` while also using `markdown.extensions.extra`**!

!!! danger "提醒"
    请记住阅读[使用说明](../usage_notes.md)，以获取使用此扩展名时可能相关的信息！

扩展:

| 扩展                              | 名称                            |
| --------------------------------- | ------------------------------- |
| [BetterEm](./betterem.md)         | `pymdownx.betterem`             |
| [SuperFences](./superfences.md)   | `pymdownx.superfences`          |
| [Footnotes][footnotes]            | `markdown.extensions.footnotes` |
| [Attribute Lists][attr-list]      | `markdown.extensions.attr_list` |
| [Definition Lists][def-list]      | `markdown.extensions.def_list`  |
| [Tables][tables]                  | `markdown.extensions.tables`    |
| [Abbreviations][abbreviations]    | `markdown.extensions.abbr`      |
| [ExtraRawHTML](./extrarawhtml.md) | `pymdownx.extrarawhtml`         |

## 选项

如果您希望通过此扩展名配置各个扩展， 您可以通过将该子扩展的设置置于与子扩展名称相同的设置值下进行配置。

```py3
extension_configs = {
    'pymdownx.extra': {
        'markdown.extensions.footnotes': {
            'BACKLINK_TEXT': 'link'
        }
    }
}
```

--8<-- "links.md"
