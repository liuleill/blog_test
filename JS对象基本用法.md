# JS对象基本用法

## 一.声明对象的两种语法

#### 1.

```
let obj = {'name':'liulei','age':18}
```

#### 2.

```
let obj = new Object({'name': liulei})
```

## 二.如何删除对象的属性

#### delete obj.xxx  //可以删除obj的xxx属性

## 三.如何查看对象的属性

查看自身属性：

```
Object.keys(obj)
```

查看自身和共有属性：

```
console.dir(obj)
```

## 四.如何修改或者增加对象的属性

#### 1.直接赋值：

```
let obj ={name:'liulei'}

obj.name='liulei'

obj['name']='liulei'
```

#### 2.变量名赋值：

```
let key ='name'

obj[key]='liulei'
```

## 五.'name' in obj 和obj.hasOwnProperty('name')的区别

区别：

共同点：两者都是查看是否有某个属性

不同点：'name' in obj 不能区分是自身属性还是共有属性，而obj.hasOwnProperty('name')可以