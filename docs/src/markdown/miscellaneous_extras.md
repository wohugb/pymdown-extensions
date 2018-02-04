# 其他附加

## 备用的Slugify

Python的Markdown的默认slugify去掉所有的Unicode字符。
为了更好地处理Unicode，已经提供了几个可选的slugify选项。
这些是非常简单的slugify选项。
有很多slugify选项，其中一些是非常复杂的。
有些人可能更喜欢使用其中的一种，但是如果你只是想要一些简单的东西，可能会满足这个要求。

### `uslugify`

为了更好地处理slu Unicode中的Unicode字符，在pymdownx.slugs.uslugify处包含slugify。
这假定您将您的HTML编码为UTF-8。
在现代浏览器中，UTF-8 Unicode应该可以。
`uslugify`并使用[`NFC`][unicode-norm]形式对Unicode进行规范化，然后去除非单字Unicode字符(`-`也可以通过)。
空格被提供的分隔符替换。
最后，整个字符串是小写的。
你可以通过`slugify`参数提交这个函数来重写Toc的默认slugify。

### `uslugify_encoded`

如果你没有将你的HTML编码为UTF-8，或者更喜欢更安全的百分比编码Unicode段落，你可以使用`pymdownx.slugs.uslugify_encoded`。
这就像[uslugify](＃uslugify)，只是它编码Unicode字符。
你可以通过`slugify`参数提交这个函数来重写Toc的默认slugify。

### `uslugify_cased`

如果你喜欢保留你的Unicode slu casing的外壳，这可能是你的slu g。
这就像[uslugify](＃uslugify)，只是它保留了原始文本的情况。
你可以通过`slugify`参数提交这个函数来重写Toc的默认slugify。

### `uslugify_cased_encoded`

如果你没有将你的HTML编码为UTF-8，或者更喜欢更安全的百分比编码的Unicode slugs *和*你更喜欢保留你的Unicode字符串，你可以使用`pymdownx.slugs.uslugify_cased_encoded`。
这就像[uslugify](＃uslugify)，只是它编码Unicode字符*和*它保留原始文本的情况。
你可以通过`slugify`参数提交这个函数来重写Toc的默认slugify。

### `gfm`

如果你正在寻找像slu G一样的GitHub，这可能适合你。
这就像[uslugify](＃uslugify)，除了ASCII字符是小写字母而Unicode字符不是。

### `gfm_encoded`

如果你正在寻找像slu G一样的GitHub，这可能适合你。
这就像[uslugify](＃uslugify)，除了百分比编码Unicode字符和ASCII字符小写，而Unicode字符不是。

--8<-- "refs.md"
