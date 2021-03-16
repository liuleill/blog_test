# JS执行时机

## 1.解释为什么如下代码会打印6个6

```javascript
let i=0
for(i=0;i<6;i++){
	setTimeout(()=>{
		console.log(i)
	},0)
}
```

答：setTimeout函数的作用是让执行内容过一会儿再打印i的值，for循环每次循环一次，就要打印一次i的值，执行了6次，当i=6的时候跳出循环，当for循环结束的时候，要打印六次i的值，而此时i的值是6，所以打印6个6



## 2.写出让上面代码打印0，1，2，3，4，5的方法

```javascript
for(let i=0;i<6;i++){
	setTimeout(()=>{
		console.log(i)
	},0)
}//打印结果：0，1，2，3，4，5
```



## 3.除了使用 for let 配合，还有什么其他方法可以打印出 0、1、2、3、4、5

```javascript
let i
for(i=0;i<6;i++){
!function (i){
     setTimeout(()=>{
        console.log(i)
     },0)   
}(i)
}
```

