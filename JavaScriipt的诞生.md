# JavaScript的诞生
### 1.JavaScript的历史
`
JavaScript最初由Netscape的Brendan Eich设计，最初将其脚本语言命名为LiveScript，后来Netscape在与Sun合作之后将其改名为JavaScript。JavaScript最初受Java启发而开始设计的，目的之一就是“看上去像Java”，因此语法上有类似之处，一些名称和命名规范也借自Java，但JavaScript的主要设计原则源自Self和Scheme。JavaScript与Java名称上的近似，是当时Netscape为了营销考虑与Sun微系统达成协议的结果。微软同时期也推出了JScript来迎战JavaScript的脚本语言。
发展初期，JavaScript的标准并未确定，同期有Netscape的JavaScript，微软的JScript和CEnvi的ScriptEase三足鼎立。为了互用性，Ecma国际（前身为欧洲计算机制造商协会）创建了ECMA-262标准（ECMAScript），两者都属于ECMAScript的实现，尽管JavaScript作为给非程序人员的脚本语言，而非作为给程序人员的脚本语言来推广和宣传，但是JavaScript具有非常丰富的特性。 [10]  1997年，在ECMA（欧洲计算机制造商协会）的协调下，由Netscape、Sun、微软、Borland组成的工作组确定统一标准：ECMA-262。完整的JavaScript实现包含三个部分：ECMAScript，文档对象模型，浏览器对象模型。 [9] 
JavaScript是甲骨文公司的注册商标。Ecma国际以JavaScript为基础制定了ECMAScript标准。JavaScript也可以用于其他场合，如服务器端编程（Node.js）。
`

### 2.JavaScript的诞生记
```
网页脚本语言到底是什么语言？网景公司当时有两个选择：一个是采用现有的语言，比如Perl、Python、Tcl、Scheme等等，允许它们直接嵌入网页；另一个是发明一种全新的语言。
这两个选择各有利弊。第一个选择，有利于充分利用现有代码和程序员资源，推广起来比较容易；第二个选择，有利于开发出完全适用的语言，实现起来比较容易。
到底采用哪一个选择，网景公司内部争执不下，管理层一时难以下定决心。
就在这时，发生了另外一件大事：1995年Sun公司将Oak语言改名为Java，正式向市场推出。
Sun公司大肆宣传，许诺这种语言可以"一次编写，到处运行"（Write Once, Run Anywhere），它看上去很可能成为未来的主宰。
网景公司动了心，决定与Sun公司结成联盟。它不仅允许Java程序以applet（小程序）的形式，直接在浏览器中运行；甚至还考虑直接将Java作为脚本语言嵌入网页，只是因为这样会使HTML网页过于复杂，后来才不得不放弃。
总之，当时的形势就是，网景公司的整个管理层，都是Java语言的信徒，Sun公司完全介入网页脚本语言的决策。因此，Javascript后来就是网景和Sun两家公司一起携手推向市场的，这种语言被命名为"Java+script"并不是偶然的。
此时，34岁的系统程序员Brendan Eich登场了。1995年4月，网景公司录用了他。
Brendan Eich的主要方向和兴趣是函数式编程，网景公司招聘他的目的，是研究将Scheme语言作为网页脚本语言的可能性。Brendan Eich本人也是这样想的，以为进入新公司后，会主要与Scheme语言打交道。
仅仅一个月之后，1995年5月，网景公司做出决策，未来的网页脚本语言必须"看上去与Java足够相似"，但是比Java简单，使得非专业的网页作者也能很快上手。这个决策实际上将Perl、Python、Tcl、Scheme等非面向对象编程的语言都排除在外了。
Brendan Eich被指定为这种"简化版Java语言"的设计师。

但是，他对Java一点兴趣也没有。为了应付公司安排的任务，他只用10天时间就把Javascript设计出来了。

由于设计时间太短，语言的一些细节考虑得不够严谨，导致后来很长一段时间，Javascript写出来的程序混乱不堪。如果Brendan Eich预见到，未来这种语言会成为互联网第一大语言，全世界有几百万学习者，他会不会多花一点时间呢？

总的来说，他的设计思路是这样的：
　　（1）借鉴C语言的基本语法；
　　（2）借鉴Java语言的数据类型和内存管理；
　　（3）借鉴Scheme语言，将函数提升到"第一等公民"（first class）的地位；
　　（4）借鉴Self语言，使用基于原型（prototype）的继承机制。
所以，Javascript语言实际上是两种语言风格的混合产物----（简化的）函数式编程+（简化的）面向对象编程。这是由Brendan Eich（函数式编程）与网景公司（面向对象编程）共同决定的。

多年以后，Brendan Eich还是看不起Java。
他说：
"Java（对Javascript）的影响，主要是把数据分成基本类型（primitive）和对象类型（object）两种，比如字符串和字符串对象，以及引入了Y2K问题。这真是不幸啊。"
把基本数据类型包装成对象，这样做是否可取，这里暂且不论。Y2K问题则是直接与Java有关。根据设想，Date.getYear()返回的应该是年份的最后两位：
```
```
　　var date1 = new Date(1999,0,1);
　　var year1 = date1.getYear();
　　alert(year1); // 99
```
但是实际上，对于2000年，它返回的是100！

```
　　var date2 = new Date(2000,0,1);
　　var year2 = date2.getYear();
　　alert(year2); // 100
```
```
如果用这个函数生成年份，某些网页可能出现"19100"这样的结果。这个问题完全来源于Java，因为Javascript的日期类直接采用了java.util.Date函数库。Brendan Eich显然很不满意这个结果，这导致后来不得不添加了一个返回四位数年份的Date.getFullYear()函数。
如果不是公司的决策，Brendan Eich绝不可能把Java作为Javascript设计的原型。作为设计者，他一点也不喜欢自己的这个作品.
```
### 3.JavaScript的10个设计缺陷
##### a.不适合开发大型程序
Javascript没有名称空间（namespace），很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。
##### b.非常小的标准库
Javascript提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。
##### c.null和undefined
null属于对象（object）的一种，意思是该对象为空；undefined则是一种数据类型，表示未定义。
```
　typeof null; // object
　typeof undefined; // undefined
  ```
  两者非常容易混淆，但是含义完全不同。
  ```
  　var foo;
　　alert(foo == null); // true
　　alert(foo == undefined); // true
　　alert(foo === null); // false
　　alert(foo === undefined); // true
  ```
##### d.全局变量难以控制
Javascript的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。
```
a = 1;
　　(function(){
　　　　b=2;
　　　　alert(a);
　　})(); // 1
　　alert(b); //2
```
##### e.自动插入行尾分号
Javascript的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。
比如，下面这个函数根本无法达到预期的结果，返回值不是一个对象，而是undefined。
```
　function(){
　　　　return
　　　　　　{
　　　　　　　　i=1
　　　　　　};
　　}
```
原因是解释器自动在return语句后面加上了分号。
```
function(){
　　　　return;
　　　　　　{
　　　　　　　　i=1
　　　　　　};
　　}
```
##### f.加号运算符
+号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。
```
　alert(1+10); // 11
　alert("1"+"10"); // 110
```
如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。
```
alert(1+"10"); // 110
alert("10"+1); // 101
```
这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。
##### g.NaN
NaN是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：
```
NaN === NaN; //false
NaN !== NaN; //true
alert( 1 + NaN ); // NaN
```
与其设计NaN，不如解释器直接报错，反而有利于简化程序。
##### h. 数组和对象的区分
由于Javascript的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。Douglas Crockford的代码是这样的：
```
　if ( arr &&typeof arr === 'object' && typeof arr.length === 'number' && !arr.propertyIsEnumerable('length')){
　　　　alert("arr is an array");
　　}
```

##### i.== 和 ===
==用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。
```
　"" == "0" // false
　　0 == "" // true
　　0 == "0" // true
　　false == "false" // false
　　false == "0" // true
　　false == undefined // false
　　false == null // false
　　null == undefined // true
　　" \t\r\n" == 0 // true
```
因此，推荐任何时候都使用"==="（精确判断）比较符。
##### j.基本类型的包装对象
Javascript有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。
```
　new Boolean(false);
　new Number(1234);
　new String("Hello World");
```
与基本数据类型对应的对象类型，作用很小，造成的混淆却很大。
```
alert( typeof 1234); // number
alert( typeof new Number(1234)); // object
```
