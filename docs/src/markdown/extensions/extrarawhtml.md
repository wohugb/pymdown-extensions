# ExtraRawHTML

## 概观

Python Markdown提供了一个额外的扩展，其功能类似于PHP Markdown Extra。
由于[`pymdownx.extra`](./extra.md)覆盖的原因，PyMdown扩展实现了自己的`extra`扩展。
为了做到这一点，Python Markdown的原始HTML解析功能（用于解析HTML块内的嵌套Markdown）必须从“extra”实现中分离出来。
之后，决定将其作为一个独立的扩展来允许那些不想使用`extra`中的所有特性的人，但是仍然希望在HTML块中使用嵌套的Markdown解析。
这基本上是Python Markdown的`extra`扩展的原始HTML解析的一个包装。
有关更多信息，请参阅[Python Markdown的额外文档][nested-markdown]。

!!! example "Raw HTML Example"

    ```html
        <div class="some-class" markdown="1">
            Some *Markdown*! :smile:
        </div>
    ```

    ```html
        <div class="some-class">
            <p>Some <em>Markdown</em>! <img alt="😄" class="emojione" src="https://cdn.jsdelivr.net/emojione/assets/3.1/png/64/1f604.png" title=":smile:">
            </p>
        </div>
    ```

--8<-- "links.md"
