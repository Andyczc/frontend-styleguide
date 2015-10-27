# 语义化
没有 `CSS` 的 `HTML` 是一个语义系统而不是 UI 系统。

通常情况下，每个标签都是有语义的，所谓语义就是你的衣服分为外套， 裤子，裙子，内裤等，各自有对应的功能和含义。所以你总不能把内裤套在脖子上吧。-- 一丝

此外语义化的 `HTML` 结构，有助于机器（搜索引擎）理解，另一方面多人协作时，能迅速了解开发者意图。

#### 常见标签语义

| 标签 | 语义 |
| -- | -- |
| `<p>` | 段落 |
| `<h1> <h2> <h3> ...` | 标题 |
| `<ul>` | 无序列表 |
| `<ol>` | 有序列表 |
| `<blockquote>` | 大段引用 |
| `<cite>` | 一般引用 |
| `<b>` | 为样式加粗而加粗 |
| `<strong>` | 为强调内容而加粗 |
| `<i>` | 为样式倾斜而倾斜 |
| `<em>` | 为强调内容而倾斜 |
| `code` | 代码标识 |
| `abbr` | 缩写 |

### HTML5 语义化

##### 新的语义化标签

| 标签 | 语义 |
| -- | -- |
| `<section>` | 定义文档中的一个章节 |
| `<nav>` | 定义只包含导航链接的章节 |
| `<article>` | 定义可以独立于内容其余部分的完整独立内容块 |
| `<aside>` | 定义和页面内容关联度较低的内容——如果被删除，剩下的内容仍然很合理 |
| `<header>` | 定义页面或章节的头部。它经常包含 logo、页面标题和导航性的目录。 |
| `<footer>` | 定义页面或章节的尾部。它经常包含版权信息、法律信息链接和反馈建议用的地址 |
| `<main>` | 定义文档中主要或重要的内容 |

> 更多详见 [HTML5 标签列表](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/HTML5/HTML5_element_list)  

##### 在不支持HTML5的浏览器器中使用HTML5

> 分节和标题元素应该在大部分的不支持HTML5的浏览器中工作。尽管不支持，但不必使用特殊的DOM接口。仅仅只需要一个特殊的CSS样式，因为未知元素默认会样式化为 `display:inline`：

```css
section, article, aside, footer, header, nav, main {
  display:block;
}
```

### 示例


更多语义化的内容，参考下列写的文章：  
> 
* [HTML5的文档节段和纲要](https://developer.mozilla.org/zh-CN/docs/Web/Guide/HTML/Sections_and_Outlines_of_an_HTML5_document)  
* [深入理解HTML5标签](http://segmentfault.com/a/1190000002695791)  
* [Dive Into HTML5 ](http://diveintohtml5.info/semantics.html?ref=driverlayer.com)   

