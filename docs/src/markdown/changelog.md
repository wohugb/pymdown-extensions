# 更新日志

## 4.8.0

2018年1月17日

- **新**: 通过`progress_increment`设置进度条类的级别增量，而不是使用`20`的硬编码值。
- **修复**: 下一个Markdown版本的兼容性更改。

## 4.7.0

2017年12月8日

- **新**: 为Arithmatex带回通用输出。现在在`generic`选项下（＃185）。
- **修复**: 在打开标签关闭之前，StripHTML应该允许空格。
- **修复**: MagicLink不应该在链接中自动链接（＃151）。

## 4.6.0

2017年12月2日

- **新**: Arithmatex now *just* uses the script wrapper output as it is the most reliable output, and now previews can be achieved by providing a span with class `MathJax_Preview` that gets auto hidden when the math is rendered. `insert_as_script`, `tex_inline_wrap`, and `tex_block_wrap` have all been deprecated as they are now entirely unnecessary. A new option has been added called `preview` that controls whether the script output generates a preview or not when the rendered math output is loading. Users no longer need to configure `tex2jax.js` in there MathJax configuration anymore. (#171)
- **新**: PlainHTML has been renamed to StripHTML. `strip_attributes` is now a list instead of a string with a default of `[]`. `pymdownx.plainhtml` is still available with the old convention for backwards compatibility, but will be removed for version 5.0. (!176)
- **修复**: PlainHTML has better script and style content avoidance to keep from stripping HTML tags and attributes from style and script content. (!174)
- **修复**: PlainHTML can strip attributes that are not quoted. (!174)

## 4.5.1

2017年11月28日

- **修复**: If an invalid provider is given, default to `github`. If no `user` or `repo` is specified, do not convert links that depend on those default values. (#169)

## 4.5.0

2017年11月26日

- **新**: Add GitLab style compare link shorthand and link shortening. (#160)
- **新**: Deprecate GitHub extension. It is now recommended to just include the extensions you want to create a GitHub feel instead of relying on a an extension to package something close-ish. (#159)

## 4.4.0

2017年11月23日

- **新**: Add social media mentions -- Twitter only right now. (#156)
- **修复**: Use correct regular expression for GitLab and Bitbucket.

## 4.3.0

2017年11月14日

- **新**: Shorthand format for referencing non-default provider commits, issues, pulls, and mentions. (!147)
- **新**: Shorthand format for mentioning a repo via `@user/repo`. (!149)
- **新**: Add repository provider specific classes. (!149)
- **新**: Make repository labels configurable. (!149)
- **修复**: Adjust pattern boundaries auto-links.

## 4.2.0

2017年11月13日

- **新**: MagicLink can now auto-link a GitHub like shorthand for repository references. (!139)
- **新**: MagicLink now renders pull request links with a slightly different output from issues. (!139)
- **新**: Deprecate `base_repo_url` in MagicLink in favor of the new `provider`, `user`, and `repo`. (!139)
- **新**: MagicLink now adds classes to repository links. (!139)
- **新**: MagicLink now adds title to repository links. (!139)
- **新**: MagicLink no longer styles repository commit hashes as code. (!143)
- **修复**: MagicLink repository link outputs now better reflect default user and repository context. (!143)
- **修复**: PlainHTML should not strip tags that are part of JavaScript code. (!140)

## 4.1.0

2017年10月11日

- **新**: Details can now have multiple classes defined.

## 4.0.0

2017年8月29日

- **新**: Details extension will now derive a title from the class if only a class is provided. (#107)
- **新**: Remove deprecated legacy emoji generator format.
- **新**: Remove deprecated `use_codehilite_settings`.
- **新**: Remove deprecated `spoilers` extension redirect.
- **新**: Update emoji databases: EmojiOne (3.1.2) and Twemoji to .(2.5.0)

## 3.5.0

Jun 13, 2017

- **新**: Add new slugs to preserve case. (!103)
- **新**: Add new GFM specific slug (both percent encoded and normal) that only lowercases ASCII chars just like GFM does. (#101)
- **修复**: PathConverter should not try and convert obscured email address (with HTML entities). (#100)
- **修复**: Don't normalize Unicode in slugs with `NFKD`, use `NFC` instead. (#98)
- **修复**: Don't let EscapeAll escape CriticMarkup placeholders.  EscapeAll will no longer escape `STX` and `ETX`; they will just pass through. (#95)
- **修复**: Replace CriticMarkup placeholders after replacing raw HTML placeholders. (#95)

## 3.4.0

Jun 1, 2017

- **新**: Renamed Spoilers to Details
- **新**: No longer attach the `spoilers` class to `details` tags.
- **新**: Provide better example of UML script in documents.

## 3.3.0

2017年5月26日

- **新**: Added support for pull request link shortening in MagicLink. (!88)
- **新**: Added new Spoilers extension. (#85)

## 3.2.1

2017年5月23日

- **修复**: Cannot set Highlight's CSS class.

## 3.2.0

2017年5月15日

- **新**: Add support for Twemoji 2.3.5.
- **新**: Update to EmojiOne 3.0.2.
- **新**: Emoji generators now also take `category` which is also no included in all indexes.
- **修复**: Excessive new lines at end of code blocks.

## 3.1.0

2017年5月7日

- **新**: Highlight extension now runs normal indented code blocks through highlighter.
- **修复**: When Pygments is disabled, `linenums` class was attached to code blocks even if `linenums` was disabled and not enabled via fence headers.

## 3.0.0

2017年4月16日

- **新**: Added Keys extension.
- **新**: Generalized custom fences (#60). `flow` and `sequence` fence are now just custom fences and can be disabled simply by overwriting the `custom_fences` setting.
- **新**: Remove deprecated `no_nl2br` in GitHub extension. (#24)
- **新**: Remove deprecated HeaderAnchor extension. (#24)
- **新**: Remove deprecated PyMdown extension. (#24)
- **新**: Remove deprecated GitHubEmoji extension. (#24)
- **新**: Remove deprecated `nested` option in SuperFences. (#24)
- **新**: Wrapper extensions (such as GitHub and Extra) can now allow setting the included sub extensions settings (#61). Workaround settings that directly set specific extensions settings has been removed.
- **新**: Deprecated `use_codehilite_settings` in SuperFences and InlineHilite and now does nothing.  The settings will be removed in the future.  If `pymdownx.highlight` is used, it's settings will be used instead of CodeHilite. Eventually, the both SuperFences and InlineHilite will require `pymdownx.highlight` to be used and will have CodeHilite support stripped.
- **修复**: Fix MathJax CDN references and usage in documentation.  MathJax CDN is shutting down and must now use Cloudflare CDN. (#63)

## 2.0.0

2017年2月12日

- **新**: SuperFences and InlineHilite can be configured via the new Highlight extension.
- **新**: InlineHilite now has all highlighting features pushed to the Highlight extension.  This removes all the CodeHilite code that used to be in it and instead relocates it to Highlight.
- **新**: Deprecate the nesting option in SuperFences.  Nesting is default and the only acceptable behavior moving forward.  The ability to turn off nesting will be removed in 3.0.

## 1.8.0

2017年1月27日

- **新**: MagicLink special repository link shortener for GitHub, GitLab, and Bitbucket. (#49)
- **修复**: GitHub asterisk emphasis should never have had smart enabled for it. (#50)
- **修复**: MagicLink fix for compatibility with wrapped symbols like `~`, `*` etc. which are commonly used.
- **修复**: MagicLink encodes emails like Python Markdown does for consistency.
- **修复**: MagicLink doesn't allow Unicode for email and does allow Unicode in a URL. (#53)
- **修复**: InlineHilite now returns a proper `etree` element so that the `attr_list` extension and function properly with it. (#48)
- **修复**: InlineHilite will no longer break if Pygments is not installed (478b410a2199d55f3e70b452516511d3810c61a5).

## 1.7.0

2017年1月21日

- **新**: Arithmatex now supports `\(...\)`, `\[...\]`, and `\begin{}...\end{}`.
- **新**: Arithmatex has an option to embed the math code in MathJax script tags.
- **修复**: Unfortunately the wrap option is now run through an HTML escaper and HTML tags can no longer be fed in this way.  Arithmatex also now wraps "wrapped" content with spans to containerize content and keep one equation from bleeding into the next.
- **修复**: Better handling of escaped Arithmatex inline tokens.
- **修复**: Better handling of escaped InlineHilite tokens.
- **修复**: Update InlineHilite and SuperFences so that the language option can accept things like `c#` and `.net` etc.
- **修复**: Snippets now removes carriage returns from imported files to prevent breakage.

## 1.6.1

2017年1月16日

- **修复**: 从Pypi安装时不要安装工具或测试文件夹。

## 1.6.0

2017年1月15日

- **新**: EscapeAll可以选择像Pandoc那样执行更多的操作，因为你可以使逃脱的换行符变成'hardbreaks`，而逃脱的空格变成`nbsp`。
- **新**: 返工差的片段格式要求用单行格式引用文件名。  添加一个块格式。  允许暂时注释行。  并允许通过在他们之后放置一个空间来逃脱他们。
- **修复**: 修复文档问题。

## 1.5.0

2017年1月13日

- **新**: 新的EscapeAll扩展。
- **新**: 用于将外部文件包含到Markdown文件中的新代码段扩展。
- **新**: Arithmatex现在有可配置的输出包装。
- **新**: PathConverter不再验证路径的存在以允许更灵活的使用。
- **新**: 当转换到相对或绝对位置时，PathConverter现在只转换相对路径。
- **新**: 改进了对PathConverter和B64路径路径标识的支持。
- **修复**: 修正了Arithmatex在数学区域内转义`$`的问题。
- **修复**: 修正了插件会追加全局变化的问题，改变了与在Markdown实例中相反的转义列表。
- **修复**: 修正了`mark`，`caret`和`tilde`扩展不能很好地模拟`betterem`内联行为的逻辑问题。
- **修复**: 批评者不应该允许逃避批评者的标记，因为它不在规范中。

## 1.4.0

2017年1月5日

- **新**: HeaderAnchor扩展现在已被弃用。,它将在未来的版本中被删除。
- **新**: HeaderAnchor不再包含在`pymdownx.github`扩展中。
- **新**: 在准备移除HeaderAnchor时，Slugify函数被移动到`pymdownx.slug`中。
- **修复**: GitHubEmoji不是“悬而未决”，而是被弃用。

## 1.3.0

2017年1月1日

- **新**: 旨在取代GitHubEmoji的新Emoji扩展。,默认情况下，它被配置为EmojiOne和Gemoji（GitHub的表情符号）。
- **新**: GitHubEmoji被弃用。,请改用Emoji扩展名。
- **新**: PyMdown扩展已被弃用。  PyMdown扩展只是一个包装，请配置所需的个人扩展（S），而不是依靠PyMdown。
- **新**: `github`扩展现在默认关闭`nl2br`，以便正确模拟GFM中的最新变化。  `no_nl2br`选项已被弃用，将来将被删除，因为它不再反映GFM的行为。

## 1.2.0

2016年11月1日

- **新**: 添加选项以更加自定义的方式输出任务列表。

## 1.1.0

2016年3月1日

- **新**: 在安装程序中添加pypi 3.5信息
- **新**: 为MagicLink扩展添加选项，允许剥离链接协议（`http：//`等）。
- **新**: 添加选项到`github`扩展名来禁止使用`nl2br`来反映GitHub Flavored Markdown的最新变化。  目前默认是遗留的（使用`nl2br`），但会显示警告。  将来，该选项将被默认为不使用`nl2br`。

## 1.0.1

2015年12月10日

- **修复**: 序号第十一，十二，十三号

## 1.0.0

2015年12月8日

- **新**: 初始发行.

--8<-- "refs.md"
