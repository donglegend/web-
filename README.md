## 1. 介绍一下css盒模型
基本概念:标准模型+IE模型

标准模型和IE模型区别

标准模型的宽度是content
IE模型的宽和高是content+padding+border


## 2. 移动端各设备页面适配怎么实现的？


## 以下代码执行结果是什么？为什么？
 第一段代码：
```javascript
var name = 'a';
function showName() {
	console.log(name);
}
function main() {
	var name = 'b';
	showName();
}
main();
```

答案: a
解析:  
   1. JavaScript在运行是分为两个步骤，先编译后执行
   2. 编译会根据所有正式声明生成词法作用域，正式声明包括标识符（var、let等），函数参数。
   3. 运行时会根据词法作用域引用变量
   一句话：函数中变量是在定义时决定的，不是在运行时
   

第二段代码：
```javascript
function fn(){
  return print()
  function print(){
    console.log('1')
  }
}
let fn2 = function fn(){
  console.log(fn)
  return print2()
  var print2 = function(){
    console.log('2')
  }
}
fn()
fn2()
```
答案：1 ,  fn函数 ,  print2 is not a function
解析： 
   1. 函数声明会加入变量放入临近的作用域中，而函数表达式会将变量放入自己的作用域中
   2. 函数声明的变量提升是可以直接调用函数的，而print2变量提升此时被初始化为undefined
   

第三段代码：
```javascript
var userInfo = {
  name: "zhangsan",
  show() {
      setTimeout(function(){
        console.log(this)
      },100)      
  },
  arrowShow(){
      setTimeout(()=>{
        console.log(this)
      },100)      
  }
}
userInfo.show()
userInfo.arrowShow()
```
答案：Window , userInfo
解析：箭头函数类似于变量不定义this，而是引用所以词法环境中的this
      这一点很重要，所以它会引用arrowShow下的this，而不是setTimeout下的windows
   
## 
   

## 3. vue相关
### 3.1 v-if与v-show的区别？
- 在切换 v-if 块时，Vue.js 有一个局部编译/卸载过程，因为 v-if 之中的模板也可能包括数据绑定或子组件。
- v-show 简单得多——元素始终被编译并保留，只是简单地基于 CSS 切换。
- v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。
### 3.2 computed 属性可以依赖那些数据做衍生计算?
- data
- props
- computed

### 3.3 computed 和 watch 主要区别？
computed 需要返回一个值作为响应属性，不支持异步操作
watch 主要用来做一些复杂的 操作，异步操作等。

### 3.4 vue中列表循环 :key 值设置用 index 和 id 有什么区别？


## vuex相关
