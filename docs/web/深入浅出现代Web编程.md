

[全栈公开课](https://fullstackopen.com/zh/)


### 开发原则
- 始终打开你的网络浏览器上的开发者控制台。在macOS上，通过_F12_或同时按下_option-cmd-i_来打开控制台。 在Windows或Linux上，通过_F12_或同时按_ctrl-shift-i_来打开控制台
- 确保Network（网络）标签打开，并选中Disable cache（禁用缓存）选项，如图。Preserve log（保存日志 也很有用：它可以在重新加载页面时保存应用打印的日志。
- Network（网络）标签显示了浏览器和服务器的通信方式
- _Console_标签
- 文档对象模型Document Object Model，或[DOM](https://en.wikipedia.org/wiki/Document_Object_Model)，是一个应用编程接口(_API_)，它能够对与网页相对应的_元素树_进行程序化修改。
- 通过在控制台标签中输入_document_来访问_document_对象。
- 层叠样式表Cascading Style Sheets，或称CSS，是一种用来决定网页外观的样式表语言。
- [AJAX](https://en.wikipedia.org/wiki/Ajax_%EF%BC%88%E7%BC%96%E7%A8%8B%EF%BC%89)(Asynchronous JavaScript and XML)使用包含在HTML中的JavaScript来获取网页内容，而不需要重新渲染网页。
- [单页应用](https://en.wikipedia.org/wiki/Single-page_application) (SPA)由一个从服务器上获取的HTML页面组成，其内容由在浏览器中执行的JavaScript来操作。
- 目前最流行的实现网络应用逻辑的浏览器端的工具是Facebook's [React](https://reactjs.org/)库。
- [前端和后端](https://en.wikipedia.org/wiki/Front_and_back_ends)。浏览器是前端，在浏览器上运行的JavaScript是前端代码。另一边，服务器则是后端。

### Part1

##### React
```
archlinux

# npm 7+, extra double-dash is needed:
npm create vite@latest part1 -- --template react

cd part1
npm install

npm run dev

```

- React组件的布局大多是用[JSX](https://reactjs.org/docs/introducing-jsx.html)编写的。虽然JSX如下所示：HTML，但我们实际上是在处理一种写JavaScript的方式。底层上，由React组件返回的JSX被编译成JavaScript。
- **React组件名称必须大写**。
- 
##### JavaScript

- JavaScript标准的官方名称是[ECMAScript](https://en.wikipedia.org/wiki/ECMAScript)。
- [Node.js](https://nodejs.org/en/)是一个基于Google's [Chrome V8](https://developers.google.com/v8/)JavaScript引擎的JavaScript运行环境，
- 代码被写入以_.js_结尾的文件中，通过键入_node name_of_file.js_命令来运行。
- Variable
```js
const x = 1 // const var
let y = 5  // var

console.log(x, y)   // 1 5 are printed
y += 10
console.log(x, y)   // 1 15 are printed
y = 'sometext'
console.log(x, y)   // 1 sometext are printed
x = 4               // causes an error
```

- Arrays
```js
const t = [1, -1, 3] //因为数组是一个对象，这个变量总是指向同一个对象。

t.push(5)

console.log(t.length) // 4 is printed
console.log(t[1])     // -1 is printed

t.forEach(value => {
  console.log(value)  // numbers 1, -1, 3, 5 are printed, each to own line
})


const t = [1, 2, 3, 4, 5]

const [first, second, ...rest] = t

```
- Object,属性的值可以是任何类型的，比如整数、字符串、数组、对象
```js
const object1 = {
  name: 'Arto Hellas',
  age: 35,
  education: 'PhD',
}

const object2 = {
  name: 'Full Stack web application development',
  level: 'intermediate studies',
  size: 5,
}

const object3 = {
  name: {
    first: 'Dan',
    last: 'Abramov',
  },
  grades: [2, 3, 5, 3],
  department: 'Stanford University',
}

console.log(object1.name)         // Arto Hellas is printed
const fieldName = 'age'
console.log(object1[fieldName])    // 35 is printed

object1.address = 'Helsinki' //add 
object1['secret number'] = 12341

```

- Function
	- 箭头函数的功能是在几年前才加入到JavaScript中的，版本[ES6](https://rse.github.io/es6-features/)。在这之前，定义函数的唯一方法是使用关键字_function_。
	- 在[函数声明](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)中给出一个名称。
	- 定义函数的方式是使用[函数表达式](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function)
```js
const sum = (p1, p2) => {
  console.log(p1)
  console.log(p2)
  return p1 + p2
}

const result = sum(1, 5)
console.log(result)

const square = p => {
  console.log(p)
  return p * p
}
const square = p => p * p
const t = [1, 2, 3]
const tSquared = t.map(p => p * p)

//before es6
function product(a, b) {
  return a * b
}
const result = product(2, 6)

const average = function(a, b) {
  return (a + b) / 2
}
const result = average(2, 5)

```

##### React_Status_Event
- _useState_React的[状态钩子](https://reactjs.org/docs/hooks-state.html)
	- 应用调用[setTimeout](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)函数并传递给它两个参数：一个用于增加计数器状态的函数和一个一秒钟的超时。
	- 作为第一个参数传递给_setTimeout_函数的函数在调用_setTimeout_函数一秒钟后被调用
	- 当修改状态的函数_setCounter_被调用时，_React重新渲染组件_，这意味着组件函数的函数体被重新执行。
```js
import { useState } from 'react'
const [ counter, setCounter ] = useState(0)

//
setTimeout(
  () => setCounter(counter + 1),
  1000
)

```
- Event

```js
const App = () => {
  const [ counter, setCounter ] = useState(0)

  return (
    <div>
      <div>{counter}</div>
      <button onClick={() => setCounter(counter + 1)}>
        plus
      </button>

      <button onClick={() => setCounter(0)}>
        zero
      </button>
    </div>
  )
}

```

##### Debug

- 在Chrome开发者控制台的_调试器_中暂停应用代码的执行，方法是在代码的任何地方写下[debugger](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/debugger)命令。一旦执行到_debugger_命令被执行的地方，执行将暂停。
- _useState_函数（以及课程后面介绍的_useEffect_函数）_不能从循环、条件表达式或任何不是定义组件的函数的地方调用_。
- 


### Part2

- console.log , props 一个对象
```js
console.log('props value is', props)
```
- map  
```js
const App = (props) => {
  const { notes } = props

  return (
    <div>
      <h1>Notes</h1>
      <ul>
        {notes.map(note =>
          <li key={note.id}>>
            {note.content}
          </li>
        )}
      </ul>
    </div>
  )
}
```