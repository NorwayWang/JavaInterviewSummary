[『Cmd 技术渲染的沙箱页面，点击此处编写自己的文档』](https://www.zybuluo.com/mdeditor "作业部落旗下 Cmd 在线 Markdown 编辑阅读器")

#<font face="宋体" color="red"><span id="qianyan">前言</span></font>
[点我跳转到锚](#mao)

# Cmd Markdown 简明语法手册

标签： Cmd-Markdown

---

### 1. 斜体和粗体

使用 * 和 ** 表示斜体和粗体。

示例：

这是 *斜体*，这是 **粗体**。
---

### 2. 分级标题

使用行首加"#"号表示不同级别的标题 (H1-H6)，标题共分6级。例如：# H1, ## H2, ### H3，#### H4。

示例：
```
#这是一个一级标题

##这是一个二级标题

### 这是一个三级标题
```
显示：
#这是一个一级标题

##这是一个二级标题

### 这是一个三级标题
---

### 3. 无序列表

使用 *，+，- 表示无序列表。

示例：

- 无序列表项 一
- 无序列表项 二
- 无序列表项 三
---

### 4. 有序列表

使用数字和点表示有序列表。

示例：

1. 有序列表项 一
2. 有序列表项 二
3. 有序列表项 三
---

### 5. 文字引用

使用 > 表示文字引用。  
\> 代表一层引用  
\>> 代表二层引用  
\>>> 代表三层引用  
依次类推  

示例：

> 代表一层引用
>> 代表二层引用
>>> 代表三层引用
---

### 6. 行内代码块

使用 \`代码` 表示行内代码块。

示例：  

让我们聊聊 `html`。
---

### 7.  代码块

使用 四个缩进空格 表示代码块。

示例：

    这是一个代码块，此行左侧有四个不可见的空格。
---

### 8. 外链接

使用 \[描述](链接地址) 为文字增加外链接，此时不显示链接网页地址。  
直接使用 链接地址，此时显示链接网页地址。

示例：

这是去往 [百度](http://www.baidu.com) 的链接。  
这是去往 [百度]:http://www.baidu.com 的链接。  
---

### 9.  插入图像

使用 \!\[描述](图片链接地址) 插入图像。  
也可以使用img标签形式插入图片，形式如下：  
`<img src="图片链接地址">描述</img>`

示例：

![我的头像](https://www.zybuluo.com/static/img/my_head.jpg)
<img src="https://www.zybuluo.com/static/img/my_head.jpg">我的头像</img>
---

### 10. 分割线

\--- 代表分割线
\*** 代表分割线

例如：
---
***

### 11. 表格支持

|项目|价格|数量|
|---|:---|:----:|
|计算机|$1600 |5  |
|手机  |$12   |12 |
|管线  |$1    |234 |
***

# Cmd Markdown 高阶语法手册

### 1. 内容目录

在段落中填写 `[TOC]` 以显示全文内容的目录结构。

[TOC]

---

### 2. 标题颜色和字体

使用font标签来设置字体，通过font标签内设置键值对来确定字体样式。face="宋体"代表了font标签对内字体使用宋体；color="red"代表指明font标签对内字体使用的颜色;size="5"代表字体大小。

例如：
一级标题颜色字体的设置
#<font face="宋体" color="red" size="5">设置标题</font>

---

### 3. 字体或图片居中

使用center标签来设置居中

例如：
<center>我是居中的文字</center>
---

### 4. <font face="宋体"><span id="mao">锚</span></font>
锚就是为了实现文章内部的跳转，使用锚需要设置两步。（与超链接类似）  
1.在跳转的目的地添加标签。  
2.在需要被设置为点击跳转的文字处，添加上步设置的标签。

例如:
[点我跳转到前言](#qianyan)
---

### 5. 删除线

使用 ~~ 表示删除线。

~~这是一段错误的文本。~~
---

### 6. 注脚

使用 [^keyword] 表示注脚。

这是一个注脚[^footnote]的样例。

这是第二个注脚[^footnote2]的样例。

---

### 7. LaTeX 公式

如果想要在Markdown文档中显示一个公式就需要先插入下面一句话。如果你熟悉Markdown文档的话，你很容易发现这实际上是插入了一个图片。

`![公式名](http://latex.codecogs.com/png.latex?这里输入您的公式)`  
上面这句话是插入一个png图片格式的公式，而下面这句话则是插入gif图片格式的公式。您可以根据自己的实际需要进行选择，这里我们选择gif图片格式。
`![公式名](http://latex.codecogs.com/gif.latex?这里输入您的公式)` 

例如:  
png图片格式的公式  
![公式名](http://latex.codecogs.com/png.latex?\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6})  

gif图片格式的公式   
![公式名](http://latex.codecogs.com/gif.latex?\sum_{i=0}^n i^2 = \frac{(n^2+n)(2n+1)}{6})


接下来我们就一起来探讨如何用纯文本表示这个公式。对于加减、等于、大于小于这种简单的算式和英文字母，因为通过键盘上现有的符号是可以表示的所有是直接输入的。譬如要表示3x+5就可以写：

`![示例](http://latex.codecogs.com/gif.latex?3x+5)`  
它的效果是： ![示例](http://latex.codecogs.com/gif.latex?3x+5)

访问[钱先生博客](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) 参考更多使用方法。

---

### 8. 加强的代码块

支持四十一种编程语言的语法高亮的显示，行号显示。

非代码示例：

```
$ sudo apt-get install vim-gnome
```

Python 示例：

```python
@requires_authorization
def somefunc(param1='', param2=0):
    '''A docstring'''
    if param1 > param2: # interesting
        print 'Greater'
    return (param2 - param1 + 1) or None

class SomeClass:
    pass

>>> message = '''interpreter
... prompt'''
```

JavaScript 示例：

``` javascript
/**
* nth element in the fibonacci series.
* @param n >= 0
* @return the nth element, >= 0.
*/
function fib(n) {
  var a = 1, b = 1;
  var tmp;
  while (--n >= 0) {
    tmp = a;
    a += b;
    b = tmp;
  }
  return a;
}

document.write(fib(10));
```

---

### 9. 流程图

#### 示例
```flow
st=>start: Start:>http://www.google.com[blank]
e=>end:>http://www.google.com
op1=>operation: My Operation
sub1=>subroutine: My Subroutine
cond=>condition: Yes
or No?:>http://www.google.com
io=>inputoutput: catch something...

st->op1->cond
cond(yes)->io->e
cond(no)->sub1(right)->op1
```


#### 更多语法参考：[流程图语法参考](http://adrai.github.io/flowchart.js/)

---

### 10. 序列图

#### 示例 1

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

#### 示例 2

```sequence
Title: Here is a title
A->B: Normal line
B-->C: Dashed line
C->>D: Open arrow
D-->>A: Dashed open arrow
```

#### 更多语法参考：[序列图语法参考](http://bramp.github.io/js-sequence-diagrams/)

---

### 11. 甘特图

甘特图内在思想简单。基本是一条线条图，横轴表示时间，纵轴表示活动（项目），线条表示在整个期间上计划和实际的活动完成情况。它直观地表明任务计划在什么时候进行，及实际进展与计划要求的对比。

```gantt
    title 项目开发流程
    section 项目确定
        需求分析       :a1, 2016-06-22, 3d
        可行性报告     :after a1, 5d
        概念验证       : 5d
    section 项目实施
        概要设计      :2016-07-05  , 5d
        详细设计      :2016-07-08, 10d
        编码          :2016-07-15, 10d
        测试          :2016-07-22, 5d
    section 发布验收
        发布: 2d
        验收: 3d
```

#### 更多语法参考：[甘特图语法参考](https://knsv.github.io/mermaid/#gant-diagrams)

---

### 12. Mermaid 流程图

```graphLR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

#### 更多语法参考：[Mermaid 流程图语法参考](https://knsv.github.io/mermaid/#flowcharts-basic-syntax)

---

### 13. Mermaid 序列图

```sequenceDiagram   
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts <br/>prevail!
    John-->>Alice: Great!
    John->>Bob: How about you?
    Bob-->>John: Jolly good!
```

#### 更多语法参考：[Mermaid 序列图语法参考](https://knsv.github.io/mermaid/#sequence-diagrams)

---

### 14. 定义型列表

名词 1
:   定义 1（左侧有一个可见的冒号和四个不可见的空格）

代码块 2
:   这是代码块的定义（左侧有一个可见的冒号和四个不可见的空格）

        代码块（左侧有八个不可见的空格）

---

### 15. Html 标签

目前支持的 HTML 元素有：
`<kbd>  <b>  <i>  <em>  <sup>  <sub>  <br>`等  

例如：`使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑`

使用 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Del</kbd> 重启电脑

例如：你可以用 Html 写一个纵跨两行的表格：
```
<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
        <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>
```

<table>
    <tr>
        <th rowspan="2">值班人员</th>
        <th>星期一</th>
        <th>星期二</th>
        <th>星期三</th>
    </tr>
    <tr>
        <td>李强</td>
        <td>张明</td>
        <td>王平</td>
    </tr>
</table>

---

### 16. 内嵌图标

本站的图标系统对外开放，在文档中输入

    <i class="icon-weibo"></i>

即显示微博的图标： <i class="icon-weibo icon-2x"></i>

替换 上述 `i 标签` 内的 `icon-weibo` 以显示不同的图标，例如：

    <i class="icon-renren"></i>

即显示人人的图标： <i class="icon-renren icon-2x"></i>

更多的图标和玩法可以参看 [font-awesome](http://fortawesome.github.io/Font-Awesome/3.2.1/icons/) 官方网站。

---

### 17. 待办事宜 Todo 列表

使用带有 [ ] 或 [x] （未完成或已完成）项的列表语法撰写一个待办事宜列表，并且支持子列表嵌套以及混用Markdown语法，例如：

    - [ ] **Cmd Markdown 开发**
        - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
        - [ ] 支持以 PDF 格式导出文稿
        - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
        - [x] 改进 LaTex 功能
            - [x] 修复 LaTex 公式渲染问题
            - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
    - [ ] **七月旅行准备**
        - [ ] 准备邮轮上需要携带的物品
        - [ ] 浏览日本免税店的物品
        - [x] 购买蓝宝石公主号七月一日的船票
        
对应显示如下待办事宜 Todo 列表：
        
- [ ] **Cmd Markdown 开发**
    - [ ] 改进 Cmd 渲染算法，使用局部渲染技术提高渲染效率
    - [ ] 支持以 PDF 格式导出文稿
    - [x] 新增Todo列表功能 [语法参考](https://github.com/blog/1375-task-lists-in-gfm-issues-pulls-comments)
    - [x] 改进 LaTex 功能
        - [x] 修复 LaTex 公式渲染问题
        - [x] 新增 LaTex 公式编号功能 [语法参考](http://docs.mathjax.org/en/latest/tex.html#tex-eq-numbers)
- [ ] **七月旅行准备**
    - [ ] 准备邮轮上需要携带的物品
    - [ ] 浏览日本免税店的物品
    - [x] 购买蓝宝石公主号七月一日的船票
        
        
[^footnote]: 这是一个 *注脚* 的 **文本**。

[^footnote2]: 这是另一个 *注脚* 的 **文本**。
