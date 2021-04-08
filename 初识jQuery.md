## 一.前言

jQuery作为JavaScript库，算是历史最长和使用范围最广的了，里面封装了很多对页面，如HTML，head，body等进行可以操作的api

## 二.jQuery具体的操作

#### 1.jQuery如何获取元素？

```
$(document)			//选择整个文档对象
$('#myId')			//选择id为myId的网页元素
$('div.myClass')	//选择class为myClass的div元素
$('input[name=first]')//选择name属性等于first的input元素

 $('a:first') //选择网页中第一个a元素
　$('tr:odd') //选择表格的奇数行
　$('#myForm :input') // 选择表单中的input元素
　$('div:visible') //选择可见的div元素
　$('div:gt(2)') // 选择所有的div元素，除了前三个
　$('div:animated') // 选择当前处于动画状态的div元素
　
　//jQuery提供了DOM树上的移动方法：
　$('div').next('p'); //选择div元素后面的第一个p元素
  $('div').parent(); //选择div元素的父元素
　$('div').closest('form'); //选择离div最近的那个form父元素
　$('div').children(); //选择div的所有子元素
　$('div').siblings(); //选择div的同级元素
　

```



#### 2.jQuery的链式操作是怎么样的

```
$('div').find('h2').eq(2).html('hello');
拆开看：
$('div')		//找到div元素
.find('h2')		//选择其中的h3元素
.html('hello') //将它的内容改为Hello
.end()			//退回h3元素那一步
.eq(0)
.html('world')
```



#### 3.jQuery如何创建元素的

```
$('<p>hello</p>');
$('<li class="new">new list item</li>')
$('ul').append('<li>list item</li>')
```



#### 4.jQuery如何移动元素的

jQuery提供了两组移动方法：

方法一：是直接移动该元素。

方法二：是移动其他元素，使得目标元素达到我们想要的位置。

**应用场景**：假定我们选中了一个div元素，需要把它移动到p元素后面。

第一种方法是使用.insertAfter()，把div元素移动p元素后面：`　$('div').insertAfter($('p'));`

第二种方法是使用.after()，把p元素加到div元素前面：`　$('p').after($('div'));`

表面上看，这两种方法的效果是一样的，唯一的不同似乎只是操作视角的不同。但是实际上，它们有一个重大差别，那就是返回的元素不一样。第一种方法返回div元素，第二种方法返回p元素。你可以根据需要，选择到底使用哪一种方法。

使用这种模式的操作方法，一共有四对：

```
.insertAfter()和.after(): 在现存元素的外部，从后面插入元素
.insertBefore()和.before():在现存元素的外部，从前面插入元素
.appendTo()和.append():在现存元素的内部，从后面插入元素
.prependTo()和.prepend():在现存元素的内部，从前面插入元素
```



#### 5.jQuery如何修改元素的

jQuery 使用同一个函数，来完成取值（getter）和赋值（setter）。具体是取值还是赋值，由参数来控制，不传参数则表示取值，传入参数则表示赋值。

常用的取值和赋值方法如下：

```
.html() //取出或设置html内容
.text() //取出或设置文本内容
.attr() //取出或设置某个属性的值
.width() //取出或设置某个元素的宽度
.height() //取出或设置某个元素的高度
.val() //取出某个表单元素的值
```

