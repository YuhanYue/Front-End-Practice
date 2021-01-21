# DOM

## 1 What's DOM

---

Document Object Model，是W3C组织推荐的处理可拓展标记语言的标准编程接口。W3C已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容、结构和样式。

## 2 DOM树

---

![DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_4.00.55_PM.png](DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_4.00.55_PM.png)

- 文档：一个页面就是一个文档(document)。
- 元素：页面中所有的标签都是元素(element)。
- 节点：网页中所有的内容都是节点（标签，属性，文本，注释等等）， DOM中使用node表示。

DOM把以上内容都看作是对象。

## 3 获取元素

---

首先要获取元素，才能操作元素。

1. 根据ID获取

    使用`getElementById()`方法获取。

    ```jsx
    <div id = 'time'>2019-9-9</div>
    <script>
    	var timer = document.getElementById('time');
    	console.log(timer);
    	//打印返回的元素对象
    	console.dir(timer);
    </script>
    ```

    此id为大小写敏感的字符串。

    找到了后返回的是一个element。

2. 根据标签名获取

根据`getElementsByTagName()`方法可以返回带有指定标签名的对象的集合。

```jsx
var lis = document.getElementsByTagName('li');
```

返回的是获取过来元素对象的集合，以伪数组的形式存储。

指定父元素，不能让伪数组形式作为父元素。

```jsx
var ol = document.getElementByTagName('ol');
console.log(ol[0].getElementByTagName('ol'));
```

3. HTML5新增获取元素的方式

```jsx
document.getElementByClassName('类名');
document.querySelector('选择器');//返回指定选择器的第一个元素对象
```

4.获取特殊元素(body, html)

```jsx
//获取body元素
document.body;

//获取html元素
document.documentElement;
```

## 4 事件基础

---

事件是可以被JavaScript侦测到的行为。简单理解为：触发-响应的机制。网页中的每个元素都可以产生某些可以触发JS的事件。

事件三要素：

1. 事件源：事件被触发的对象。（按钮）
2. 事件类型：如何触发？onClick? onPress?
3. 事件处理程序：通过函数赋值完成。

常见的鼠标事件：

![DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_4.46.55_PM.png](DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_4.46.55_PM.png)

## 5 操作元素

---

JS的DOM操作可以改变网页内容、结构和样式，我们可以利用DOM操作元素来改变元素里的内容、属性等。

 

1. 改变元素内容

    ```jsx
    //element.innerText
    //element.innerHTML
    ```

    innerText从起始位置到种植位置的内容，但它去除html标签，同时空格和换行也会去掉。

    innerHTML从起始位置到终止位置的全部内容，包括html抱歉，同时保留空格和换行。

    innerText不识别HTML标签。🏷️

2. 常用元素的属性操作

![DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_5.05.07_PM.png](DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-20_at_5.05.07_PM.png)

3. 表单元素的属性操作

利用DOM可以操作如下表单元素的属性：

type、value、checked、selected、disabled

 

4. 样式属性操作

可以通过JS修改元素的大小、颜色、位置等样式。

![DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-21_at_8.38.14_AM.png](DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-21_at_8.38.14_AM.png)

- display: none
- display: block

    ClassName会直接修改类名！如果想要保留原先的类名→多类名选择器：

    ```jsx
    this.className = 'firs change';//原先的类名是change
    ```

操作元素总结：

操作元素是DOM的核心内容。

![DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-21_at_9.59.20_AM.png](DOM%200f52a966eb624ce88f373af06bed49d3/Screen_Shot_2021-01-21_at_9.59.20_AM.png)

排他思想：首先排除掉其他人，然后设置自己的样式。 

- 自定义属性

`getAttribute()` 来得element属性。自己添加的属性称为自定义属性。

`setAttribute()` 更改属性。

- H5自定义属性

    自定义属性目的：是为了保存并使用某些数据，有些数据可以保存到页面中而不用保存到数据库中。