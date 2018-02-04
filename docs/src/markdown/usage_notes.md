# 使用说明

## 不兼容的扩展

PyMdown扩展包括三个扩展，旨在**替换**默认Python Markdown扩展中的对应部分。
您不必使用PyMdown扩展的所有扩展， 但如果您选择使用下面的一个包, 你应该使用它而不是Python的Markdown之一; **他们不能在同一时间加载**.

另外，您不应该多次包含扩展名。
如果您尝试同时包含多个扩展程序，则可能会收到意想不到的结果。
此外，请注意，某些分机是包含多个分机的便利分机;请注意它们包含的内容，以免您不小心重新包含它们。

- `pymdownx.superfences` 取代 `markdown.extensions.fenced_code`.

- `pymdownx.betterem` 取代 `markdown.extensions.smartstrong`.

- `pymdownx.extra` 取代 `markdown.extensions.extra`, 但要记住, `pymdown.extra`是一个方便的扩展，它只是一个包装，包含了许多扩展。请记住避免包括这个，然后包括冲突的扩展名或扩展名的双打。以下是包含的扩展的完整列表:

    ```
    'markdown.extensions.tables',
    'pymdownx.magiclink',
    'pymdownx.betterem',
    'pymdownx.tilde',
    'pymdownx.emoji',
    'pymdownx.tasklist',
    'pymdownx.superfences'
    ```

- `pymdownx.github`不能代替任何扩展名，只是一个方便的扩展，包括获得GitHub-ish感觉所需的大部分扩展。请记住避免包括这个，然后包括冲突的扩展名或扩展名的双打。以下是包含的扩展的完整列表:

    ```
    'markdown.extensions.tables',
    'pymdownx.magiclink',
    'pymdownx.betterem',
    'pymdownx.tilde',
    'pymdownx.emoji',
    'pymdownx.tasklist',
    'pymdownx.superfences'
    ```
