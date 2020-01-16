#<font face="宋体" color="red" size="5"><span id="qianyan">前言</span></font>
[点我跳转到锚](#mao)

# Markdown 简明语法手册

标签： Markdown

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
# 这是一个一级标题

## 这是一个二级标题

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

![我的头像](http://hbimg.b0.upaiyun.com/9414d81388fc99e0d072f1041ace3551237f00763de6-Q09JCY_fw658)
<img src="http://hbimg.b0.upaiyun.com/9414d81388fc99e0d072f1041ace3551237f00763de6-Q09JCY_fw658">我的头像</img>
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

# Markdown 高阶语法手册

### 1. 锚
锚就是为了实现文章内部的跳转，使用锚需要设置两步。（与超链接类似）  
1.在跳转的目的地添加标签。  
2.在需要被设置为点击跳转的文字处，添加上步设置的标签。

例如:
[点我跳转到前言](#qianyan)
---

### 2. 删除线

使用 ~~ 表示删除线。

~~这是一段错误的文本。~~
---

### 3. 加强的代码块

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

### 4. Html 标签

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

### 5. 待办事宜 Todo 列表

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
