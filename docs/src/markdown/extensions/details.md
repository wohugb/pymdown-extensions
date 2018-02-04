# Details(细节)

## 概观

详细信息是创建可隐藏内容的可折叠元素的扩展,它使用HTML5`#!html <details> <summary>`标签来实现这一点。 它支持嵌套，你也可以强制默认状态打开。如果你想要设计一些不同于其他的样式，你可以选择自定义的类。

## 句法

在开始之前，细节必须包含一个空行。 如果要启动默认状态为“打开”的详细信息块，请使用`???`启动详细信息块或`???+`。  用可选的一个或多个类（以空格分隔）和包含在引号中的摘要跟随块的开头。 内容放在标题下方，并且必须缩进。

```
??? optional-class "Summary"
    Here's some content.
```

```
??? multiple optional-class "Summary"
    Here's some content.
```

!!! example "示例详细信息"

    ```
    ???+ note "开放式的细节"

        ??? danger "嵌套的细节!"
            还有更多的内容。
    ```

    ???+ note "开放式的细节"

        ??? danger "嵌套的细节!"
            还有更多的内容。

也可以只提供一个类。如果这样做，标题将从*first*类派生。

!!! example "标题的示例类"

    ```
    ??? success
       内容。
    ```

    ??? success
        内容。

    ```
    ??? warning classes
       内容。
    ```

    ??? warning classes
        内容。

详细信息将以下面的格式输出。 内容将始终封装在某种标签中。

```html
<details class="optional-class"><summary>文本</summary><p>内容</p></details>
```

## 浏览器支持

不幸, 由于`#!html <details> <summary>`标签有多新，并不是所有的浏览器都支持它们.
为了让他们在所有新的浏览器支持, 您将不得不提供一些备用样式和JavaScript，直到所有浏览器赶上.

这个扩展的目标不是为你提供完美的polyfill, 但这是提供基本支持的基本范例.
还有更多精心制作的支持jQuery的polyfills, 添加键盘事件，甚至支持回到IE8.
随意修改这里或找到适合您的需求的解决方案。

??? settings "Basic Polyfill Setup"
    这是可以使用的基本CSS。
    这意味着在两个支持`#!html <details><summary>`标签的浏览器中提供一致的CSS，而不支持`。

    ```css
    details {
      display: block;
    }

    details[open] > summary::before {
      content: "\25BC";
    }

    details summary {
      display: block;
      cursor: pointer;
    }

    details summary:focus {
      outline: none;
    }

    details summary::before {
      content: "\25B6";
      padding-right: 0.5em;
    }

    details summary::-webkit-details-marker {
      display: none;
    }

    /* Attach the "no-details" class to details tags
       in browsers that do not support them to get
       open/show functionality. */
    details.no-details:not([open]) > * {
      display: none;
    }

    details.no-details:not([open]) summary {
      display: block;
    }
    ```

    下面是JavaScript将检测不支持 `#!html <details> <summary>` 标签的浏览器，并将“no-details”类应用于这些浏览器中的所有细节。
    它还将附加一个点击事件，将切换打开状态。
    上面的CSS将定位 `no-details` 类和 `open` 属性来隐藏/显示 `#!html <details>` 标签的内容。
    加载HTML内容后，只需运行代码。

    有很多东西没有在这里覆盖，比如跳到一个封闭的polyfilled细节元素中的脚注或ID，但这是留给用户去弄清楚的，或者是一个完整的第三方polyfill。

    ```js
    (function () {
    'use strict';
    /**
     * Converts details/summary tags into working elements in browsers that don't yet support them.
     * @return {void}
     */
    var details = (function () {

      var isDetailsSupported = function () {
        // https://mathiasbynens.be/notes/html5-details-jquery#comment-35
        // Detect if details is supported in the browser
        var el = document.createElement("details");
        var fake = false;

        if (!("open" in el)) {
          return false;
        }

        var root = document.body || function () {
          var de = document.documentElement;
          fake = true;
          return de.insertBefore(document.createElement("body"), de.firstElementChild || de.firstChild);
        }();

        el.innerHTML = "<summary>a</summary>b";
        el.style.display = "block";
        root.appendChild(el);
        var diff = el.offsetHeight;
        el.open = true;
        diff = diff !== el.offsetHeight;
        root.removeChild(el);

        if (fake) {
          root.parentNode.removeChild(root);
        }

        return diff;
      }();

      if (!isDetailsSupported) {
        var blocks = document.querySelectorAll("details>summary");
        for (var i = 0; i < blocks.length; i++) {
          var summary = blocks[i];
          var details = summary.parentNode;

          // Apply "no-details" to for unsupported details tags
          if (!details.className.match(new RegExp("(\\s|^)no-details(\\s|$)"))) {
            details.className += " no-details";
          }

          summary.addEventListener("click", function (e) {
            var node = e.target.parentNode;
            if (node.hasAttribute("open")) {
              node.removeAttribute("open");
            } else {
              node.setAttribute("open", "open");
            }
          });
        }
      }
    });

    (function () {
      var onReady = function onReady(fn) {
        if (document.addEventListener) {
          document.addEventListener("DOMContentLoaded", fn);
        } else {
          document.attachEvent("onreadystatechange", function () {
            if (document.readyState === "interactive") {
              fn();
            }
          });
        }
      };

      onReady(function () {
        details();
      });
    })();

    }());
    ```
