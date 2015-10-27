# 通用约定

### 代码风格

##### [必须] 使用 `2` 个空格做为一个缩进层级，不允许使用 `4` 个空格 或 `tab` 字符。

示例：

```html
<ul>
  <li>first</li>
  <li>second</li>
</ul>
```

##### [必须] 每行不得超过 `120` 个字符。

解释：
> 
过长的代码不容易阅读与维护。但是考虑到 HTML 的特殊性，不做硬性要求。

##### [必须] 属性的定义，统一使用双引号。

```html
<!-- 不推荐 -->
<span id='j-hook' class=text>Google</span>

<!-- 推荐 -->
<span id="j-hook" class="text">Google</span>
```

##### [必须] `class` 必须单词全字母小写，单词间以 `-` 分隔。同项目必须保持风格一致。

##### [必须] `class` 必须代表相应模块或部件的内容或功能，不得以样式信息进行命名。

示例：

```html
<!-- 推荐 -->
<div class="sidebar"></div>

<!-- 不推荐 -->
<div class="left"></div>
```

##### [必须] 元素 `id` 必须保证页面唯一。

解释：
> 
同一个页面中，不同的元素包含相同的 id，不符合 id 的属性含义。并且使用 document.getElementById 时可能导致难以追查的问题。

##### [建议] `id`、`class` 命名，在避免冲突并描述清楚的前提下尽可能短。

示例：

```html
<!-- 推荐 -->
<div id="nav"></div>
<!-- 不推荐 -->
<div id="navigation"></div>

<!-- 推荐 -->
<p class="comment"></p>
<!-- 不推荐 -->
<p class="com"></p>

<!-- 推荐 -->
<span class="author"></span>
<!-- 不推荐 -->
<span class="red"></span>
```

##### [建议] class 应以功能或内容命名，不以表现形式命名；

##### [必须] 禁止为了 `hook 脚本`，创建无样式信息的 `class`。

解释：
> 
不允许 class 只用于让 JavaScript 选择某些元素，class 应该具有明确的语义和样式。否则容易导致 css class 泛滥。

示例：

```html
<!-- 不推荐 -->
<div class="j-hook left contentWrapper"></div>

<!-- 推荐 -->
<div id="j-hook" class="sidebar content-wrapper"></div>
```

使用 id、属性选择作为 hook 是更好的方式。


##### [必须] 同一页面，应避免使用相同的 `name` 与 `id`。

解释：
> 
IE 浏览器会混淆元素的 id 和 name 属性， document.getElementById 可能获得不期望的元素。所以在对元素的 id 与 name 属性的命名需要非常小心。

一个比较好的实践是，为 id 和 name 使用不同的命名法。

示例：

```html
<input name="foo">
<div id="foo"></div>
<script>
// IE6 将显示 INPUT
alert(document.getElementById('foo').tagName);
</script>
````

### 标签
1. 自闭合（self-closing）标签，无需闭合 ( 例如： `img` `input` `br` `hr` 等 )；
2. 可选的闭合标签（closing tag），需闭合 ( 例如：`</li>` 或 `</body>` )；
3. 尽量减少标签数量；

```html
<img src="images/google.png" alt="Google">
<input type="text" name="title">

<ul> 
  <li>Style</li>
  <li>Guide</li>
</ul>

<!-- 不推荐 -->
<span class="avatar">
  <img src="...">
</span>

<!-- 推荐 -->
<img class="avatar" src="...">
```

### 属性顺序

> HTML 属性应该按照特定的顺序出现以保证易读性。

* id
* class
* name
* data-xxx
* src, for, type, href
* title, alt
* aria-xxx, role

```html
<a id="..." class="..." data-modal="toggle" href="###"></a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

### 嵌套
`a 不允许嵌套 div`这种约束属于语义嵌套约束，与之区别的约束还有严格嵌套约束，比如`a 不允许嵌套 a`。

严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样。

**语义嵌套约束**
* `<li>` 用于 `<ul>` 或 `<ol>` 下；
* `<dd>`, `<dt>` 用于 `<dl>` 下；
* `<thead>`, `<tbody>`, `<tfoot>`, `<tr>`, `<td>` 用于 `<table>` 下；

**严格嵌套约束**
* inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
* `<a>`里不可以嵌套交互式元素`<a>`、`<button>`、`<select>`等;
* `<p>`里不可以嵌套块级元素`<div>`、`<h1>~<h6>`、`<p>`、`<ul>/<ol>/<li>`、`<dl>/<dt>/<dd>`、`<form>`等。

更多详情，参考[WEB标准系列-HTML元素嵌套](http://www.smallni.com/element-nesting/)

### 布尔值属性
HTML5 规范中 `disabled`、`checked`、`selected` 等属性不用设置值。
```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
  <option value="1" selected>1</option>
</select>
```
