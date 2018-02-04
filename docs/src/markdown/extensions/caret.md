# Caret

## 概观

Caret optionally adds two different features which are syntactically built around the `^` character. The first is **insert** which inserts `#!html <ins></ins>`.  The second is **superscript** which inserts `#!html <sup></sup>` tags.

## 插

To wrap content in an **insert** tag, simply surround the text with double `^`. You can also enable `smart_insert` in the [options](#options). Smart behavior of **insert** models that of [BetterEm](betterem.md#differences).

???+ example "Insert Example"

    ```
    ^^Insert me^^
    ```

    ^^Insert me^^

## Superscript

To denote a superscript, you can surround the desired content in single `^`.  It uses Pandoc style logic, so if your superscript needs to have spaces, you must escape the spaces.

!!! example "Superscript Example"

    ```
    H^2^0

    text^a\ superscript^
    ```

    H^2^0

    text^a\ superscript^

## 选项

选项            | 类型 | 默认     | 描述
-------------- | ---- | ------- | -----------
`smart_insert` | bool | True    | 使用插入字符的智能逻辑。
`insert`       | bool | True    | 启用插入功能。
`superscript`  | bool | True    | 启用上标功能。
