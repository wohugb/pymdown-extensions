# Critic

## 概观

Critic is an extension that adds handling and support of [Critic Markup][critic-markup] which uses a special syntax to represent edits to a Markdown document.  This extension runs before all other extensions to parse the critic edits.

Critic allows you to automatically accept edits or reject the edits and render the output accordingly. It also allows for visually displaying the changes in HTML output ([mileage may vary](#limitations-with-previewing-critic-markup)).

## 用法

Critic Markup uses special markup to insert, delete, substitute, highlight, and comment.

To insert or remove text you can use `#!critic-markup {++insert me++}` and `#!critic-markup {--remove me--}` respectively.  You can also denote a substitution with `#!critic-markup {~~substitute this~>with this~~}`.

You can also highlight specific text with `#!critic-markup {==highlight me==}`. Or even comment, which is generally done by highlighting text and following it with a comment: `#!critic-markup {==highlight me==}{>>Add a comment<<}`.

!!! example "Critic Markup Accept Example"

    ```critic-markup
    Here is some {--*incorrect*--} Markdown.  I am adding this{++ here++}.  Here is some more {--text
     that I am removing--}text.  And here is even more {++text that I
     am ++}adding.{~~

    ~>  ~~}Paragraph was deleted and replaced with some spaces.{~~  ~>

    ~~}Spaces were removed and a paragraph was added.

    And here is a comment on {==some
     text==}{>>This works quite well. I just wanted to comment on it.<<}. Substitutions {~~is~>are~~} great!

    General block handling.

    {--

    * test remove
    * test remove
    * test remove
        * test remove
    * test remove

    --}

    {++

    * test add
    * test add
    * test add
        * test add
    * test add

    ++}
    ```

    --8<-- "critic-accept-example.md"

When previewing, you can style them to stand out (see [CSS](#css) for more information):

!!! example "Critic Markup Preview Example"

    ```critic-markup
    Here is some {--*incorrect*--} Markdown.  I am adding this{++ here++}.  Here is some more {--text
     that I am removing--}text.  And here is even more {++text that I
     am ++}adding.{~~

    ~>  ~~}Paragraph was deleted and replaced with some spaces.{~~  ~>

    ~~}Spaces were removed and a paragraph was added.

    And here is a comment on {==some
     text==}{>>This works quite well. I just wanted to comment on it.<<}. Substitutions {~~is~>are~~} great!

    General block handling.

    {--

    * test remove
    * test remove
    * test remove
        * test remove
    * test remove

    --}

    {++

    * test add
    * test add
    * test add
        * test add
    * test add

    ++}
    ```

    --8<-- "critic-preview-example.md"

## 预览评论标记的局限性

Parsing CriticMarkup is very straight forward.  If you need to reject critic marks or accept them, the Critic extension will work quite well.  But when trying to render the edits visually **and** trying to convert the document to HTML, things can get ugly.  I think this is the one unfortunate problem with CriticMarkup.  The existence of the critic edits can alter the actual source.  Its a fantastic idea, but it should be understood that when using CriticMarkup beyond inline or block paragraphs, there is a possibility that invalid HTML will be created for the preview (especially in relation to lists or if breaking up Markdown syntax).  I think Fletcher said it best here: http://fletcher.github.io/MultiMarkdown-4/criticmarkup.

The Critic extension does its best by employing a preprocessor to inject the critic tags before all other parsing and a post-processor to clean up some of the weird side effects of the injection (only selected odd cases as others are more difficult to fix).  It injects some classes into the edit region's HTML output which allows for CSS styling.  There is probably a lot more post-processing that could be done to fix more issues, but whether this extension will be going further down that road has not yet been decided.

## CSS

Critic renders the CriticMarkup with the following classes.

Classes   | Description
--------- |------------
`critic`  | This is applied to all critic edits.
`break`   | This is applied to critic inserts or deletes that encompass **only** 2+ newlines.
`block`   | Applied to critic HTML tags that are detected as surrounding a block region.
`comment` | A CriticMarkup comment.

??? settings "Basic CSS Setup"

    ```css
    /* Critic Markup */
    .markdown-body .critic {
      font-family: inherit;
      -webkit-border-radius: 3px;
      -moz-border-radius: 3px;
      border-radius: 3px;
      border-style: solid;
      border-width: 1px;
      padding-top: 0.1em;
      padding-bottom: 0.1em;
      text-decoration: none;
    }

    .markdown-body .critic:before,
    .markdown-body .critic:after {
      content: '\00a0';
      padding-top: 0.1em;
      padding-bottom: 0.1em;
      font-size: initial;
    }

    .markdown-body .block:before,
    .markdown-body .block:after {
      content: '';
    }

    .markdown-body mark.critic {
      border-color: #ff8600;
      background: #ffddaa;
    }

    .markdown-body ins.critic {
      border-color: #00bb00;
      background: #ddffdd;
    }

    .markdown-body del.critic {
      border-color: #dd0000;
      background: #ffdddd;
    }

    .markdown-body ins.break,
    .markdown-body del.break {
      font-size: 0;
      border: none;
    }

    .markdown-body ins.break:before,
    .markdown-body del.break:before {
      content: '\00a0\b6\00a0';
      -webkit-border-radius: 3px;
      -moz-border-radius: 3px;
      border-radius: 3px;
    }

    .markdown-body ins.after,
    .markdown-body del.after {
      content: '';
    }

    .markdown-body ins.break:before {
      color: #00bb00;
      border: 1px solid #00bb00;
      background: #ddffdd;
    }

    .markdown-body del.break:before {
      color: #bb0000;
      border: 1px solid #bb0000;
      background: #ffdddd;
    }

    .markdown-body span.critic {
      background: #ddddff;
      border: 0;
      border-top: 1px solid #0000bb;
      border-bottom: 1px solid #0000bb;
    }

    .markdown-body span.critic:before,
    .markdown-body span.critic:after {
      font-size: inherit;
      background: #ddddff;
      border: 1px solid #0000bb;
    }

    .markdown-body span.critic:before {
      content: '\00a0\bb';
      border-right: none;
      -webkit-border-top-left-radius: 3px;
      -moz-border-top-left-radius: 3px;
      border-top-left-radius: 3px;
      -webkit-border-bottom-left-radius: 3px;
      -moz-border-bottom-left-radius: 3px;
      border-bottom-left-radius: 3px;
    }

    .markdown-body span.critic:after {
      content: '\ab\00a0';
      border-left: none;
      -webkit-border-top-right-radius: 3px;
      -moz-border-top-right-radius: 3px;
      border-top-right-radius: 3px;
      -webkit-border-bottom-right-radius: 3px;
      -moz-border-bottom-right-radius: 3px;
      border-bottom-right-radius: 3px;
    }

    .markdown-body .block {
      display: block;
      padding: .02em;
    }
    ```

## 选项

Option    | Type   | Default     | Description
--------- |------- | ----------- | -----------
`mode`    | string | `#!py3 view` | `view`只是解析标记并将其显示在与HTML等效的呈现中。  `accept` 删除批评标记，并用建议的更改替换它们.  `reject` 拒绝所有的建议，并将评论标记替换为原文。

--8<-- "links.md"
