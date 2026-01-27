---
date: 2025-08-14
up:
  - "[[Javascript]]"
---
# 基础
## 变量
- var 变量
**引入作用域概念**：
- let 可变变量
- const 不可变变量
## 函数
### 箭头函数
```js
// ES5
var x = function(x, y) {
     return x * y;
}
 
// ES6
const x = (x, y) => x * y;
```
！箭头函数没有this
### 闭包
保护函数的私有变量
```js
var add = (function () {
    var counter = 0;
    return function () {return counter += 1;}
})();
//让counter只能被add访问，并且数值会被记住
```
## DOM
#### HTML
```js
document.getElementById("p1").innerHTML="新文本!";

document.getElementById("image").src="landscape.jpg";
```
#### CSS
```js
document.getElementById("p2").style.color="blue";
```
#### # HTML DOM事件
- onclick
- onload/onunload 进入/离开页面
- onchange 改变输入
- onmouseover/onmouseout
#### Eventlistener
JavaScript从HTML标记中分离开来，可读性更强
```js
//添加
document.getElementById("myBtn").addEventListener("click", displayDate);
//移除
element.removeEventListener("mousemove", myFunction);
```
#### DOM元素
```js
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);

var element = document.getElementById("div1"); element.appendChild(para);
```
# 现代JS（ES6+）关键特性
## 解构赋值
从数组或对象中提取值，并直接赋值给独立的变量
- ​对象解构 `const { prop1, prop2 } = obj;
- ​数组解构 `const [first, second] = arr;`​
- 参数解构 `function MyComponent({ name, age }) {...}` 
## 模版字符串
使用反引号`` ` ``​​定义的字符串，可以嵌入表达式和多行文本
- 嵌入表达式`${expression}` 
- 多行字符串
## 扩展语法
使用 `...`操作符，展开数组或对象的元素/属性。用于集合的复制、合并、参数传递等。
### 数组扩展
```js
// 数组合并 (创建新数组)
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]
const combinedWithExtra = [0, ...arr1, 3.5, ...arr2, 7]; // [0, 1, 2, 3, 3.5, 4, 5, 6, 7]

// 复制数组 (浅拷贝)
const arrCopy = [...arr1]; // [1, 2, 3] (修改 arrCopy 不会影响 arr1)
arrCopy.push(4);
console.log(arr1); // [1, 2, 3]
console.log(arrCopy); // [1, 2, 3, 4]

// 函数参数传递
function sum(a, b, c) { return a + b + c; }
const nums = [10, 20, 30];
console.log(sum(...nums)); // 60 (等同于 sum(10, 20, 30))

// 添加新元素 (避免 .push 修改原数组)
const newNumbers = [...numbers, 6]; // 添加末尾
const newNumbersFront = [0, ...numbers]; // 添加开头
```
### 对象扩展
```js
const person = { name: 'Mike', age: 40 };
const address = { city: 'London', country: 'UK' };

// 对象合并 (创建新对象)
const userProfile = { ...person, ...address };
console.log(userProfile); // { name: 'Mike', age: 40, city: 'London', country: 'UK' }

// 添加新属性
const updatedPerson = { ...person, occupation: 'Developer' };
console.log(updatedPerson); // { name: 'Mike', age: 40, occupation: 'Developer' }

// 更新属性 (覆盖同名属性)
const updatedAge = { ...person, age: 41 }; // { name: 'Mike', age: 41 }
console.log(updatedAge);

// 覆盖 & 添加新属性
const withEmail = { ...person, age: 41, email: 'mike@example.com' };
console.log(withEmail); // { name: 'Mike', age: 41, email: 'mike@example.com' }

// 浅拷贝对象
const personCopy = { ...person }; // 修改 personCopy 不会影响 person
```
## 模块化
- export
- import
## 数组方法
- `map()`: ​**​（用于将数据数组映射为React元素数组)​**​
- `filter()`: 过滤数组元素
- `find()`/ `findIndex()`: 查找元素/索引
- `some()`/ `every()`: 检查元素是否满足条件
- `forEach()`: 遍历（避免在 JSX 中直接使用）
- `reduce()`/ `reduceRight()`: 累积（功能强大，但优先级低于上述方法）
- `slice()`: 创建子数组副本
- `concat()`: 合并数组（可被扩展语法替代）
### map()
创建一个新数组，其结果是该数组中的每个元素是调用一次提供的函数后的返回值。
**​用途：​**​ 数据 -> 元素列表。生成组件列表。
```js
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2); // [2, 4, 6]
const squared = numbers.map((num, index) => `Index ${index}: ${num * num}`); // 带索引
// React 渲染列表
const items = ['Apple', 'Banana', 'Cherry'];
const listItems = items.map((item) => <li key={item}>{item}</li>); // 生成 <li> 元素数组
// 在组件中：
return <ul>{listItems}</ul>; // 渲染列表
```
## 对象方法

## 异步编程
js是单线程语言，为了不阻塞主线程（UI渲染等），I/O操作（网络请求、文件读写、定时器）需要异步处理。
**演进：​**​ Callback（回调地狱） -> Promise（链式调用） -> async/await（同步写法处理异步）。
### 回调函数 Callback
最简单的异步模式：将函数作为参数传递给另一个函数，在操作完成后调用它（作为回调）。
​**​缺点：​**​ 嵌套回调过多导致“回调地狱”，难以阅读和维护。
```js
function fetchData(callback) {
  setTimeout(() => { // 模拟网络请求
    callback('Data received!');
  }, 1000);
}
fetchData((data) => {
  console.log(data); // 1秒后输出 'Data received!'
  // 如果这里再调用另一个异步函数，就会开始嵌套...
});
```
### Promise
表示一个异步操作的最终完成（或失败）及其结果值。
**优点：​**​ 链式调用，解决回调地狱。错误处理更集中。
```js
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const success = Math.random() > 0.5;
      if (success) {
        resolve('Success data!');
      } else {
        reject(new Error('Failed to fetch!'));
      }
    }, 1000);
  });
}
// 使用 Promise
fetchData()
  .then(data => {
    console.log('Got data:', data);
    return processData(data); // processData 如果返回 Promise，可以继续 .then
  })
  .then(processed => {
    console.log('Processed:', processed);
  })
  .catch(error => {
    console.error('Error:', error.message);
  });
```
### async/await(语法糖，首选写法)​​

- `async`: 声明一个函数是异步函数。该函数总是返回一个 ​**​Promise​**​。如果函数内 return 一个非Promise值，async 函数会用 `Promise.resolve()`将其包装成 Promise。
- `await`: 只能在 `async`函数内部使用。它会​**​暂停​**​ async 函数的执行，等待一个 Promise 解决（成功或失败），然后返回解决后的值。 
- **​优点：​**​ 代码​**​扁平化​**​，逻辑更清晰，错误处理用 `try/catch`（像处理同步错误一样）。
```js
async function fetchUserData(userId) {
  try {
    const response = await fetch(`https://api.example.com/users/${userId}`); // 等待fetch请求完成
    if (!response.ok) { // 检查响应是否成功
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const userData = await response.json(); // 等待解析JSON数据
    console.log('User data:', userData);
    return userData; // 返回解析后的数据 (会被包装在由async函数自动返回的Promise中)
  } catch (error) {
    console.error('Failed to fetch user:', error);
    throw error; // 再次抛出错误，让调用此函数的代码可以通过 .catch 捕获
  }
}
// 调用 async 函数
fetchUserData(123)
  .then(data => console.log('Processed in then:', data))
  .catch(err => console.error('Handled error:', err));

// 或者在另一个 async 函数中调用:
async function doSomething() {
  const user = await fetchUserData(123);
  // 拿到 user 后继续操作...
}
```