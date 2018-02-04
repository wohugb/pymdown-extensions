# Mark

## 概观

Mark添加了插入`#!html <mark></ mark>`标签的功能。
语法要求文本被双等号包围。
它可以选择配置为使用智能逻辑。
**标记**的智能和非智能变体的语法行为[BetterEm](betterem.md#differences).

要标记一些文本，只需用双`=`来包围文本即可。

!!! example "Mark 例"

    ```
    ==mark me==

    ==smart==mark==
    ```

    ==mark me==

    ==smart==mark==

## 选项

| 选项         | 类型 | 类型         | 描述                     |
| ------------ | ---- | ------------ | ------------------------ |
| `smart_mark` | bool | `#!py3 True` | 使用智能逻辑与标记字符。 |
