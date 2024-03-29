# 基本原则

### 本文档声明

在本文档中，使用的关键字会以中文 + 括号包含的关键字英文表示：必须（MUST）。
> 关键字 `"MUST"`, `"MUST NOT"`, `"REQUIRED"`, `"SHALL"`, `"SHALL NOT"`, `"SHOULD"`, `"SHOULD NOT"`, `"RECOMMENDED"`, `"MAY"`, 和 `"OPTIONAL"` 被定义在[rfc2119](http://www.ruanyifeng.com/blog/2007/03/rfc2119.html)中。

本文档的目的是统一团队间编码风格，降低团队间代码交流及维护成本，总结编码最佳实践。

### 结构、样式、行为分离

[建议] 尽量确保文档和模板只包含 `HTML` 结构，样式都放到样式表里，行为都放到脚本里。

### 缩进

[必须] 统一 **两个空格** 缩进，不得使用 `Tab` 或者 `Tab`、空格混搭。
> 用 **[.editconfig](http://editorconfig.org/)** 文件来对IDE强制规范  
```
indent_style = space  
indent_size = 2
```

### 文件编码

[必须] **使用不带 `BOM` 的 UTF-8 编码。**
1. 在 HTML中指定编码 `<meta charset="utf-8">` ；
2. *无需* 使用 `@charset` 指定样式表的编码，它默认为 `UTF-8` （参考 [@charset](https://developer.mozilla.org/en-US/docs/Web/CSS/@charset)）；

### 一律使用小写字母
```html
<!-- 推荐 -->
<img src="google.png" alt="Google">

<!-- 不推荐 -->
<A HREF="/">Home</A>
```

```css
/* 推荐 */
color: #e5e5e5;

/* 不推荐 */
color: #E5E5E5;
```

### 省略外链资源 URL 协议部分

[建议] 省略外链资源（图片及其它媒体资源）URL 中的 `http` / `https` 协议，使 URL 成为相对地址，避免 [Mixed Content](https://developer.mozilla.org/zh-CN/docs/Security/MixedContent) 问题，减小文件字节数。**其它协议（`ftp` 等）的 URL 不省略。**

```html
<!-- 推荐 -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- 不推荐 -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
```

```css
/* 推荐 */
.example {
  background: url(//www.google.com/images/example);
}

/* 不推荐 */
.example {
  background: url(http://www.google.com/images/example);
}
```

### 统一注释

通过配置编辑器，可以提供快捷键来输出一致认可的注释模式。

##### HTML 注释
- 模块注释
```html
<!-- 文章列表列表模块 -->
<div class="article-list">
...
</div>
```

- 区块注释 【待商榷】
```html
<!--
@name: Drop Down Menu
@description: Style of top bar drop down menu.
@author: Ashu(Aaaaaashu@gmail.com)
-->
```

##### CSS 注释

组件块和子组件块以及声明块之间使用一空行分隔，子组件块之间两空行分隔；【待商榷】

```css
/*
 * 组件块
 * 组件块描述
 * -------------------------------------------------- 
 */

// 子组件块
// ==================================================
.selector {
  padding: 15px;
  margin-bottom: 15px;
}


// 子组件块
// ==================================================
.selector-secondary {
  display: block; 
}

.selector-three {
  display: span; /* 注释 */
}
```

##### JavaScript / AnguarJS 注释 【参见angular.js源码注释】
- 单行注释

  *必须* 独占一行。`//` 前后跟一个空格，缩进与下一行被注释说明的代码一致。

- 多行注释

  避免使用 `/*...*/` 这样的多行注释。有多行注释内容时，使用多个单行注释。

- 函数/方法注释
  1. 函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识。；
  1. 参数和返回值注释必须包含类型信息和说明；
  1. 当函数是内部函数，外部不可访问时，可以使用 ```@inner``` 标识；

```javascript
/**
 * 函数描述
 *
 * @param {string} p1 参数1的说明
 * @param {string} p2 参数2的说明，比较长
 *     那就换行了.
 * @param {number=} p3 参数3的说明（可选）
 * @return {Object} 返回值描述
 */
function foo(p1, p2, p3) {
    var p3 = p3 || 10;
    return {
        p1: p1,
        p2: p2,
        p3: p3
    };
}
```

- 文件注释

文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 应该提供文件的大体内容, 它的作者, 依赖关系和兼容性信息。如下:

```javascript
/**
 * @fileoverview Description of file, its uses and information
 * about its dependencies.
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2015 Meizu Inc. All Rights Reserved.
 */
```

### 代码验证
* 使用 [W3C HTML Validator](http://validator.w3.org/) 来验证你的HTML代码有效性；
* 使用 [W3C CSS Validator](http://jigsaw.w3.org/css-validator/validator.html.zh-cn) 来验证你的CSS代码有效性；

代码验证不是最终目的，真的目的在于让开发者在经过多次的这种验证过程后，能够深刻理解到怎样的语法或写法是非标准和不推荐的，即使在某些场景下被迫要使用非标准写法，也可以做到心中有数。
