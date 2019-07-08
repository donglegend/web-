## 1. 介绍一下css盒模型
盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border).

有两种， IE 盒子模型、标准 W3C 盒子模型；IE的content部分包含了 border 和 pading;


## 2. 移动端各设备页面适配怎么实现的？
可以通过 rem 或者 vw|vh来实现页面适配，
要求还原度不高的情况下，也可以使用 css3的媒体查询


## 3. 以下代码执行结果是什么？为什么？
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
   
## 4. 什么是跨域请求？怎样解决？
跨域，指的是浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对JavaScript施加的安全限制。

所谓同源是指，域名，协议，端口均相同，浏览器执行js脚本的时候，会检查这个脚本属于哪一个页面，如果不是同源页面，就不会执行

解决方法

- jsonp（jsonp 的原理是动态插入 script 标签）
- 服务器设置反向代理
- 服务端 setHeader("Access-Control-Allow-Origin", "*");
- document.domain + iframe
- window.name、window.postMessage

## 5. 请描述一下 cookie 以及其优缺点

cookie虽然在持久保存客户端数据提供了方便，分担了服务器存储的负担，但还是有很多局限性的。 第一：每个特定的域名下最多生成20个cookie

1.IE6或更低版本最多20个cookie 2.IE7和之后的版本最后可以有50个cookie。 3.Firefox最多50个cookie 4.chrome和Safari没有做硬性限制 IE和Opera 会清理近期最少使用的cookie，Firefox会随机清理cookie。

cookie的最大大约为4096字节，为了兼容性，一般不能超过4095字节。

IE 提供了一种存储可以持久化用户数据，叫做uerData，从IE5.0就开始支持。每个数据最多128K，每个域名下最多1M。这个持久化数据放在缓存中，如果缓存没有清理，那么会一直存在。

优点：极高的扩展性和可用性

1.通过良好的编程，控制保存在cookie中的session对象的大小。 2.通过加密和安全传输技术（SSL），减少cookie被破解的可能性。 3.只在cookie中存放不敏感数据，即使被盗也不会有重大损失。 4.控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。

缺点： 1.Cookie数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。

2.安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。

3.有些状态不可能保存在客户端。例如，为了防止重复提交表单，我们需要在服务器端保存一个计数器。如果我们把这个计数器保存在客户端，那么它起不到任何作用。
  
   

## 6. vue相关
### v-if与v-show的区别？
- 在切换 v-if 块时，Vue.js 有一个局部编译/卸载过程，因为 v-if 之中的模板也可能包括数据绑定或子组件。
- v-show 简单得多——元素始终被编译并保留，只是简单地基于 CSS 切换。
- v-if 有更高的切换消耗而 v-show 有更高的初始渲染消耗。因此，如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好。
### computed 属性可以依赖那些数据做衍生计算?
- data
- props
- computed

### computed 和 watch 主要区别？
computed 需要返回一个值作为响应属性，不支持异步操作
watch 主要用来做一些复杂的 操作，异步操作等。

### vue中列表循环 :key 值设置用 index 和 id 有什么区别？


## 7. vuex相关
解释一下对 action 和 mutation 的理解？

