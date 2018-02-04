# MagicLink

## 概观

MagicLink是一个扩展，提供了一些有用的链接相关的功能。
MagicLink可以自动链接HTML，FTP和电子邮件链接。
它可以自动转换存储库链接(GitHub，GitLab和Bitbucket)，并以更简洁，简洁的格式显示它们。
MagicLink也可以配置为直接自动链接上述速记格式。

如果碰巧遇到特定情况的语法冲突，则可以始终使用旧的自动链接格式:`#!md <https://www.link.com>`。
如果启用，库链接缩短也将应用于括号内的自动链接格式。

## 自动链接

MagicLink支持自动链接HTTP，FTP和电子邮件链接。
您可以在原始文本中指定这些链接，并且应该自动链接。
MagicLink有一些限制，使其不能自动链接不属于链接的文本。
如果您有一个无法检测到的链接，您可以随时使用旧式尖括号链接格式:`#!md <https://www.link.com>`。

!!! example "自动链接示例"

    ```
    - 只需将链接直接粘贴到文档中即可:https://google.com。
    - 甚至是一个电子邮件地址:fake.email@email.com。
    ```

    - 只需将链接直接粘贴到文档中即可:https://google.com。
    - 甚至是一个电子邮件地址:fake.email@email.com。

## 速记链接

MagicLink支持GitHub，GitLab和Bitbucket问题(#1)，提取/合并请求(!13)，提交(7d1b1902ea7fe00043a249564ed5032f08dd7152)的速记引用，并比较
您也可以参考存储库(@facelessuser/pymdown-extensions)，它支持提到用户(@facelessuser)。
提及也适用于社交媒体(目前只支持Twitter)。

提及也适用于社交媒体(目前只支持Twitter)。
选择GitLab作为其语法弥合了三个提供者之间的差距。
GitLab和Bitbucket需要一个特定的语法，而GitHub没有。
我也更喜欢GitLab的提交引用中的细微差别，因为它符合pull和issue语法。

### 配置

要启用代码存储库提供程序和社交媒体提供程序的简写语法，请在[options](#options)中分别启用`repo_url_shorthand`和`social_url_shorthand`。

要使用此功能，您必须首先在[选项](#选项)中指定所有简写引用所在的`提供者`
如果你指定一个代码仓库提供者作为你的默认值，你还必须指定`user`和`repo`(仓库)，它增加了更多的上下文，并且允许你缩短与默认`user`有关的问题的语法,和/或`回购`。
如果您使用MagicLink为其中一个受支持的代码存储库提供程序托管的项目编写文档，这非常有用。

如果您更普遍地使用这个扩展，那么将社交媒体提供者设置为默认的`提供者`可能更有意义。
没有必要为社交媒体提供商设置`用户`或`回购`，因为上下文对提及没有用处。
如果启用，您仍然可以使用简写形式引用存储库链接，尽管格式较长。

!!! warning
    链接没有被验证，因此请确保您指定有效的问题，存储库和用户，因为它们将被自动链接，即使它们无效。

### 提到

链接没有被验证，因此请确保您指定有效的问题，存储库和用户，因为它们将被自动链接，即使它们无效。
要引用非默认提供者，请使用格式`@{provider}:{user}`

!!! example "提例"

    ```
    @facelessuser

    @twitter:twitter
    ```

    @facelessuser

    @twitter:twitter

对于代码存储库提供者，你也可以提到存储库。
这个特性实际上是受GitHub扩展@Python-Markdown/github-links的启发，它执行*类似*
使用提及自动链接存储库的语法与自动链接用户非常相似，不同之处在于您将存储库附加到用户名如下:`@{user}/{repo}`。
如果指定一个非默认的提供者，那么这个表单看起来像:`@{provider}:{user}/{repo}`。
存储库的输出省略了@符号，只会显示用户和存储库，但是您可以自由地使用CSS进行样式设置，使其更像本文档中所做的那样突出。

!!! example "存储库提示示例"

    ```
    @facelessuser/pymdown-extensions

    @gitlab:pycqa/flake8
    ```

    @facelessuser/pymdown-extensions

    @gitlab:pycqa/flake8

### 问题和请求

问题和拉取请求分别用`#{num}`和`!{num}`指定。
要为默认用户下的非默认存储库指定问题，请在存储库前加上:{{repo}#{num}`。
要在非默认用户下指定一个存储库，请在用户和存储库前缀:`{user}/{repo}#{num}`。
要引用外部提供者，请使用`{provider}:{user}/{repo}#{num}`格式。
要引用外部提供者，请使用`{provider}:{user}/{repo}#{num}`格式。

!!! example "问题示例"

    ```
    Issue #1

    Issue backrefs#1

    Issue Python-Markdown/markdown#1

    Issue gitlab:pycqa/flake8#385

    Pull request !13

    Pull request backrefs!4

    Pull request Python-Markdown/markdown!598

    Pull request gitlab:pycqa/flake8!213
    ```

    Issue #1

    Issue backrefs#1

    Issue Python-Markdown/markdown#1

    Issue gitlab:pycqa/flake8#385

    Pull request !13

    Pull request backrefs!4

    Pull request Python-Markdown/markdown!598

    Pull request gitlab:pycqa/flake8!213

!!! note "Note"

    GitHub实际上给出了pull请求并发出唯一的值，而GitLab和Bitbucket可以使用相同的ID作为问题。
    所以对于GitHub，您可以使用`#{num}`格式解决问题，并且GitHub会将您重定向到适当的问题或拉。

    GitLab和Bitbucket **必须指定不同的问题，因此是`!13`格式。
    虽然GitHub不需要*使用拉格式，你可以如果你喜欢。
    这种格式实际上是从GitLab中借用的。

### 提交

提交简写语法只是40个字符的提交哈希值:`{哈希}`。
非常类似于问题和拉取请求，可以使用`{repo}@{hash}``在默认用户下使用`{user}/{repo}@{hash} ,。
最后，要引用外部提供者，请使用格式`{provider}:{user}/{repo}@{hash}`。
如果默认提供者是社交媒体提供者，则只能使用后者的语法。

!!! example "提交示例"

    ```
    181c06d1f11fa29961b334e90606ed1f1ec7a7cc

    backrefs@cb4ecc5e7d8f7cdff0bb4482174f2ff0dcc35c61

    Python-Markdown/markdown@de5c696f94e8dde242c29d4be50b7bbf3c17fedb

    gitlab:pycqa/flake8@8acf55e0f85233c51c291816d73d828cc62d30d1
    ```

    181c06d1f11fa29961b334e90606ed1f1ec7a7cc

    backrefs@cb4ecc5e7d8f7cdff0bb4482174f2ff0dcc35c61

    Python-Markdown/markdown@de5c696f94e8dde242c29d4be50b7bbf3c17fedb

    gitlab:pycqa/flake8@8acf55e0f85233c51c291816d73d828cc62d30d1

### DIFF/比较

GitLab提供了一个有用的简写来指定链接来比较两个提交之间的差异。
所有支持的存储库提供者都采用了这一点。

指定一个比较链接与指定一个提交链接非常相​​似，除了你必须指定旧的哈希和由`...`分隔的新的哈希:{{hash1} ... {hash2}`。
要为默认用户下的非默认存储库指定比较，请在存储库的前缀:{{repo}@{hash1} ... {hash2}`。
要在非默认用户下指定比较，请在用户和存储库前缀:`{user}/{repo}@{hash1} ... {hash2}`。
最后，要引用外部提供者，请使用`{provider}:{user}/{repo}@{hash1} ... {hash2}`格式。

!!! example "比较例子"

    ```
    e2ed7e0b3973f3f9eb7a26b8ef7ae514eebfe0d2...90b6fb8711e75732f987982cc024e9bb0111beac

    backrefs@88c6238a1c2cf71a96eb9abb4b0213f79d6ca81f...cb4ecc5e7d8f7cdff0bb4482174f2ff0dcc35c61

    Python-Markdown/markdown@007bd2aa4c184b28f710d041a0abe78bffc0ec2e...de5c696f94e8dde242c29d4be50b7bbf3c17fedb

    gitlab:pycqa/flake8@1ecf97005a024391fb07ad8941f4d25c4e0aae6e...9bea7576ac33a8e4f72f87ffa81dfa10256fca6e
    ```

    e2ed7e0b3973f3f9eb7a26b8ef7ae514eebfe0d2...90b6fb8711e75732f987982cc024e9bb0111beac

    backrefs@88c6238a1c2cf71a96eb9abb4b0213f79d6ca81f...cb4ecc5e7d8f7cdff0bb4482174f2ff0dcc35c61

    Python-Markdown/markdown@007bd2aa4c184b28f710d041a0abe78bffc0ec2e...de5c696f94e8dde242c29d4be50b7bbf3c17fedb

    gitlab:pycqa/flake8@1ecf97005a024391fb07ad8941f4d25c4e0aae6e...9bea7576ac33a8e4f72f87ffa81dfa10256fca6e

## 存储库链接缩短器

MagicLink还可以识别问题，拉取请求，提交和比较链接，并以与[资源库快捷链接](#简写链接)功能相同的输出格式呈现它们。
不幸的是，由于MagicLink不使用任何提供者的API来验证用户链接，所以不提供链接缩短目前不被支持，并且一些合法链接可以看起来像用户链接，但不是。

如果我们从外部提供商指定长格式的URL，他们将被适当缩短。


!!! example "外部提供者示例"

    ```
    - https://gitlab.com/pycqa/flake8/issues/385
    - https://bitbucket.org/mrabarnett/mrab-regex/issues/260/extremely-slow-matching-using-ignorecase
    ```

    - https://gitlab.com/pycqa/flake8/issues/385
    - https://bitbucket.org/mrabarnett/mrab-regex/issues/260/extremely-slow-matching-using-ignorecase

当指定引用配置的`provider`，`user`和`repo`的链接时，根据上下文，链接将被缩短。

!!! example "内部提供者示例"

    ```
    - https://github.com/facelessuser/pymdown-extensions/issues/1
    - https://github.com/facelessuser/pymdown-extensions/pull/13
    - https://github.com/facelessuser/pymdown-extensions/commit/3f6b07a8eeaa9d606115758d90f55fec565d4e2a
    - https://github.com/facelessuser/pymdown-extensions/compare/e2ed7e0b3973f3f9eb7a26b8ef7ae514eebfe0d2...90b6fb8711e75732f987982cc024e9bb0111beac
    - https://github.com/facelessuser/Rummage/commit/181c06d1f11fa29961b334e90606ed1f1ec7a7cc
    ```

    - https://github.com/facelessuser/pymdown-extensions/issues/1
    - https://github.com/facelessuser/pymdown-extensions/pull/13
    - https://github.com/facelessuser/pymdown-extensions/commit/3f6b07a8eeaa9d606115758d90f55fec565d4e2a
    - https://github.com/facelessuser/pymdown-extensions/compare/e2ed7e0b3973f3f9eb7a26b8ef7ae514eebfe0d2...90b6fb8711e75732f987982cc024e9bb0111beac
    - https://github.com/facelessuser/Rummage/commit/181c06d1f11fa29961b334e90606ed1f1ec7a7cc

## CSS

对于正常的链接，没有类被添加到锚标签。
对于存储库链接，`magiclink`将被添加为一个类。
此外，还会为每个存储库链接类型和提供程序添加一个额外的类。

Link\ Type           | Class
-------------------- | -----
General              | `magiclink`
Mentions             | `magiclink-mention`
Repository\ Mentions | `magiclink-repository`
Issues               | `magiclink-issue`
Pulls                | `magiclink-pull`
Commits              | `magiclink-commit`
Compares             | `magiclink-compare`
GitHub               | `magiclink-github`
Bitbucket            | `magiclink-bitbucket`
GitLab               | `magiclink-gitlab`
Twitter              | `magiclink-twitter`

## 选项

选项                          | 类型   | 默认         | 描述
------------------------------- | ------ | --------------- | -----------
`hide_protocol`                 | bool   | `#!py3 False`    | 如果为`真`，链接将显示为不含最初的`ftp://`，`http://`，`https://`或`ftps://`。
`repo_url_shortener`            | bool   | `#!py3 False`    | 如果`True`，GitHub，Bitbucket和GitLab提交，拉取和问题链接都以简写语法呈现。
`repo_url_shorthand`            | bool   | `#!py3 False`    | 如果是`True`，则可以直接使用简写语法来表示提交，提取，发布和提及存储库提供程序的链接，并且它们将被自动链接。
`social_url_shorthand`          | bool   | `#!py3 False`    | 如果为`True`，则可以直接使用简写语法来表示社交媒体提供商的提及链接，并且它们将被自动链接。
`provider`                      | string | `#!py3 'github'` | 提供程序用于存储库简写语法和缩写。
`user`                          | string | `#!py3 ''`       | 用于指定提供程序的默认用户名。
`repo`                          | string | `#!py3 ''`       | 用于指定用户和提供者的默认存储库名称。
`labels`                        | dict   | `#!py3 {}`       | 用于覆盖存储库链接标题文本的字典。有关更多信息，请参阅[标签](#标签)。
!!! warning "弃用4.2.0"
    在4.2.0中，`base_repo_url`已经被弃用，用于`provider`，`user`和`repo`。
    如果启用了`repo_url_shorthand`，`base_repo_url`将被忽略，`provider`，`user`和`repo`将被使用。

    ``base_repo_url`将在未来某个时候被删除。,请迁移到`provider`，`user`和`repo`。

### 标签

默认情况下，MagicLink以`{provider} {label}:{info}`的形式为存储库链接提供标题。
您可以通过配置`labels`选项为`{label}`指定不同的值。

默认值是:

```js
    {
        'commit': 'Commit',
        'compare': 'Compare',
        'issue': 'Issue',
        'pull': 'Pull Request',
        'mention': 'User',
        'repository': 'Repository'
    }
```

您只需提供您想要覆盖的选项。
假设我们想要采用GitLab术语来提取请求，我们可以简单地将`labels`设置为:

```js
    {
        'pull': 'Merge Request'
    }
```

--8<-- "refs.md"
