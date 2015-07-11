# Front end convention


## HTML

  1. [HTML content type](#content-type)
  1. [HTML标签语义](#html-syntax)
  1. [代码缩进](#indent)
  1. [页内CSS位置](#css-position)
  1. [页内Javascript位置](#javascript-position)
  

## CSS
  1. [盒子模型](#box-model)
  1. [样式分行](#css-line)
  1. [样式位置](#css-location)
  1. [stylus嵌套结构](#stylus-nested)
 

## Javacript
  1. [分号](#semicolon)
  1. [引号](#quote)
  1. [判断和比较](#comparison-operators--equality)
  1. [变量命名约定](#naming-convention)
  1. [变量和函数位置](#var-position)
  1. [读取属性](#get-property)


### <a name="content-type"></a> HTML content type

  - 使用HTML5文件类型

    ```html
    <!DOCTYPE HTML>
    <html>
    <head>
      <meta charset="UTF-8">
      <title></title>
    </head>
    <body>
      
    </body>
    </html>

    ```

### <a name="html-syntax"></a> HTML标签语义

  - 使用语义HTML标签

    ```html

    <!-- bad -->
    <div class="nav">
      <p><a>page1</a></p>
      <p><a>page2</a></p>
    </div>

    <!-- good -->
    <ul class="nav">
      <li><a>page1</a></li>
      <li><a>page2</a></li>
    </ul>


    <!-- bad -->
    <span style="cursor:pointer">点击打开<span>

    <!-- good -->
    <a href="javascript:;">点击打开</a>


    <!-- bad -->
    <!-- divist -->
    <div class="shipping-wrapper">
      <div class="name"></div>
      <div class="meta">
        <div class="address"></div>
      </div>
      <div class="desc"></div>
    </div>

    <!-- good -->
    <section class="wrapper">
      <cite></cite>
      <span class="meta">
        <address></address>
      </span>
      <div class="desc"></div>
    </section>

    ```

### <a name="indent"></a> 代码缩进

  - 使用两个空格（适用HTML、CSS、Javacript）


### <a name="css-position"></a> 页内CSS位置

  - 放在`<head>`标签内

    ```html
    /* bad */
    <div>
      <style>
        .foo {
          color: #000;
        }
      </yle>
    </div>

    /* good */
    <head>
      <style>
        .foo {
          color: #000;
        }
      </style>
    </head>

    ```

### <a name="javascript-position"></a> 页内Javascript位置

  - `<script>` 根级代码不缩进

    ```html
    /* bad */
    <section>
      <div>
        <h1>Foobar</h1>
        <script>
          $('h1').html('gotcha.')
        </script>
      </div>
    </section>

    /* good */
    <section>
      <div>
        <h1>Foobar</h1>
    <script>
    $('h1').html('gotcha.')
    </script>
      </div>
    </section>

    ```

### <a name="box-model"></a> 盒子模型

  - 使用content-box作为开发默认值

    ```css
    /* bad */
    box-sizing: content-box;

    /* good */
    * {
      box-sizing: border-box;
    }

    ```

### <a name="css-line"></a> 样式分行

  - 样式属性一个一行

    ```css
    /* bad */
    .body { background: #ddd; color: #333 }

    /* good */
    .body {
      background: #ddd;
      color: #333 
    }

    ```

### <a name="css-location"></a> 样式位置

  - 每个样式都有各自的作用域

    ```css
    /* bad */
    将有样式都写在main.css文件内

    /* good */
    如果样式不是通用样式，将样式写在页面的<head>标签内

    ```

### <a name="stylus-nested"></a> Stylus样式结构

  - 自身样式在前，嵌套样式在后

    ```css
    /* bad */
    .navigation
      .h2
         color: #333
      width: 300px
      display: none

    /* good */
    .navigation
      width: 300px
      display: none

      .h2
        color: #333

    ```

## Javacript

### <a name="semicolon"></a> 分号

  - 我们不使用分号。除了行首是"[,(,+,-,/"，在前面添加分号

    ```javascript
    // bad
    var dom = document.getElementById('foo');
    dom.style.display = 'none';

    // good
    var dom = document.getElementById('foo')
    dom.style.display = 'none'

    ```

### <a name="quote"></a> 引号

  - 尽量使用单引号

    ```javascript
    // bad
    var pizza = "yummy"
    var hamburg = "'yummy'?"

    // good
    var pizza = 'yummy'
    var hamburg = '"yummy"?'
    ```

### <a name="comparison-operators--equality"></a> 判断和比较

  - 使用严格检查 ===, !== 而不是 ==, !=

    ``` javascript

    // bad
    if (name !== '') {
      // ...stuff...
    }

    // good
    if (name) {
      // ...stuff...
    }

    // bad
    if (collection.length > 0) {
      // ...stuff...
    }

    // good
    if (collection.length) {
      // ...stuff...
    }
    ```

### <a name="naming-convention"></a> 命名约定

  - 避免使用单个字母作为变量，尽可能使用有意义的变量名。

    ``` javascript

    // bad
    function q() {
      // ...stuff...
    }

    // good
    function query() {
      // ..stuff..
    }
    ```

  - 使用驼峰命名法

    ```javascript
    // bad
    var this_is_my_object = {}
    function c() {}
      var u = new user({
      name: 'Bob Parr'
    })

    // good
    var thisIsMyObject = {}
    function thisIsMyFunction() {}
      var user = new User({
      name: 'Bob Parr'
    })
    ```

  - 类名使用帕斯卡命名法

    ```javascript
    // bad
    function user(options) {
      this.name = options.name
    }
                              
    var bad = new user({
      name: 'nope'
    })
                              
    // good
    function User(options) {
      this.name = options.name
    }
                              
    var good = new User({
      name: 'yup'
    })
    ```

### <a name="var-position"></a> 变量和函数位置

  - 变量->函数->调用

    ```javascript
    // bad

    var name = 'foo'
    greet(name)

    function greet(name) {
      alert(name)
    }

    // good
    var name = 'foo'
    function greet(name) {
      alert(name)
    }
    greet(name)
    ```

### <a name="get-property"></a> 读取属性

  - 使用`点语法`读取属性

    ```javascript
    var person = {
      name: 'Kelly'
    }

    // bad
    person['name']

    // good
    person.name

    ```
