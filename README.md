## 1. 介绍一下css盒模型
基本概念:标准模型+IE模型

标准模型和IE模型区别

标准模型的宽度是content
IE模型的宽和高是content+padding+border


## 2. 移动端各设备页面适配怎么实现的？


## 以下代码执行结果是什么？为什么？
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
