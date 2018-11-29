### 缩进

  - 2 空格，为了更好适应 git 的显示效果和减少多层缩进影响。

  - 函数参数需要换行时，与函数名缩进 2 空格，对象数组相同。如：

    ```js
    const ex = (
      template, style, javascript, image,
    ) => {}

    const obj = {
      key1,
      key2,
      ...
    }
    ```

<br/>

### 符号

  - 单引号由于双引号。

  - 多行对象与数组的最后一项总是添加逗号。如：

    ```js
    const items = [
      'item1',
      'item2',
    ]

    ```

  - 总是省略分号。避免歧义时请在语句前添加分号。如：

    ```js
    ...}}}
    // 避免歧义时，语句前添加分号
    ;(() => { code... })()
    ```

  - 三元表达式换行时符号在行前。

  - 单个函数参数时可以省略括号：`const num = x => { ... }`

  - 单行语句可以省略大括号，如：`const num = x => x + x`

<br/>

### 其他格式

  - 大括号不换行。

  - 在文档和注释中，英文或符号的左右两侧留半角空格。

  - 声明多个变量时，请增加空格：`let num = 1, name = ''`

  - 变量命名请勿使用下划线 `_`，文件命名请勿使用大写字符，常量命名尽可能使用大写。

<br/>

### 编程风格

  - 使用 `const` 优先于 `let`，不要使用 `var`。

  - 优先使用字面量方式声明变量。

  - 使用函数表达式由于函数声明：

    ```js
    // bad
    function flatArray() {}

    // good
    const flatArray = function() {}
    ```

  - 优先使用箭头函数。

  - 使用 `===`，不要使用 `==`。

  - 优先使用函数。使用 `forEach` 代替 Loop，当能够使用功能性迭代函数时 (`map / reduce / filter ...`)，优先使用，这样有助于统一风格和降低代码量。

  - 减少魔术字符串/数字：

    ```js
    // bad
    const paintBigBook = (book, color) => {
      if (book.pages > 100) {
        book.color = color
      }
    }

    // good
    const PAINT_LIMIT = 100
    const isBigBook = (book, limit) => book.pages > limit
    const paintBigBook = (book, color, limit) => {
      if (isBigBook(book, limit)) {
        book.color = color
      }
    }
    paintBigBook(book, color, PAINT_LIMIT)

    ```

  - 在可能的情况下，使用 `return` 减少缩进：

    ```js
    // bad
    const paintBigBook = (book, color, limit) => {
      if (isBigBook(book, limit)) {
        book.color = color
      }
    }

    // good
    const paintBigBook = (book, color, limit) => {
      if (!isBigBook(book, limit)) return
      book.color = color
    }


    // bad
    if (arg) {
      ...
    } else {
      ...
    }

    // good
    if (arg) {
      ...
      return
    }
    ...
    ```

<br/>

### 编程建议

  - 尽可能提升代码纯度，减少副作用：

    ```js
    // bad
    let x = 5
    const add = num => num + x

    // good
    const add = (num, x) => num + x
    ```

  - 减少内存使用：

    ```js
    // bad
    for (...) {
      let count = 0
      count = count + item.size
      ...
    }

    // good
    let count = 0
    for (...) {
      count = 0
      count = count + item.size
      ...
    }
    ```

  - 使代码更富有语义化：

    ```js
    // bad
    if (page.index === 5) { ... }

    // good
    const isMemberPage = page.index === 5
    if (isMemberPage) { ... }
    ```

<br/>

### 禁止使用

  - 禁止使用 `arguments` / `eval` / `with`。禁止在生产中使用 `debugger。

  - 禁止在非函数中使用 `return`。




